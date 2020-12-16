---
description: Tips and Tricks. This is for windows
---

# Tips for installing

## Getting Yearn Exporter Working

### Things you will need

* [Infura account to query the blockchain with](https://infura.io/login) - For brownie
* Python
* Brownie
* etherscan account and [api key](https://etherscan.io/myapikey)
  * Add `ETHERSCAN_TOKEN` as a variable in windows under user variables
  * Make its value your Api-Key Token

![](.gitbook/assets/envirvari.jpg)

* If using Yearn-Exporter on your own computer and not a pre-made docker implementation \(to be released\) then you will need your own Infura Key. This has a 100k request limit and yearn-exporter is currently not optimized for multi-calls as of yet; therefore, you will need to skip some blocks to stay within the free account limits. I have found that sleeping for 250 ms should be sufficient. Modify `yearn.py`as follows.

{% tabs %}
{% tab title="Python" %}
```python
import warnings, time
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Python" %}
```python
def exporter_v1():
    prom_gauge = Gauge("yearn", "yearn stats", ["vault", "param"])
    timing = Gauge("yearn_timing", "", ["vault", "action"])
    start_http_server(8800)
    registry = vaults_v1.load_registry()
    # load vaults once, todo: update params
    with timing.labels("registry", "load").time():
        vaults = vaults_v1.load_vaults(registry)
    for block in chain.new_blocks():
        secho(f"{block.number}", fg="green")
        for vault in vaults:
            with timing.labels(vault.name, "describe").time():
                try:
                    info = vault.describe()
                except ValueError as e:
                    print("error", e)
                    continue
            for param, value in info.items():
                # print(f'{param} = {value}')
                prom_gauge.labels(vault.name, param).set(value)
        time.sleep(250)
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Python" %}
```python
def exporter_v2():
    vault_gauge = Gauge("yearn_vault", "", ["vault", "param"])
    strat_gauge = Gauge("yearn_strategy", "", ["vault", "strategy", "param"])
    timing = Gauge("yearn_timing", "", ["vault", "action"])
    start_http_server(8801)
    for block in chain.new_blocks():
        secho(f"{block.number}", fg="green")
        for vault in vaults_v2.VAULTS:
            secho(vault.name)
            with timing.labels(vault.name, "describe").time():
                info = vault.describe()

            for param, value in info.items():
                if param == "strategies":
                    continue
                vault_gauge.labels(vault.name, param).set(value)

            for strat in info["strategies"]:
                for param, value in info["strategies"][strat].items():
                    strat_gauge.labels(vault.name, strat, param).set(value)
        time.sleep(250)
```
{% endtab %}
{% endtabs %}

The time.sleep\(\) functions have been added to the exporter\_v1 and v2 methods, along with importing time at the top of the file. You can adjust sleep time to your preference and visit your infura project dashboard to view how often calls are happening. 

