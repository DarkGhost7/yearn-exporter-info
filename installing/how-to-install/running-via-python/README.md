---
description: Tips and Tricks. This is for windows
---

# Running via Python

### Things you will need

## Infura

* [Infura account to query the blockchain with](https://infura.io/login) 
  * For brownie
  * Make a project and put in the secret and project id after the =
  * Run cmd and type the code below and add in your newly generated keys

{% tabs %}
{% tab title="CMD" %}
```text
set WEB3_INFURA_API_SECRET=
set WEB3_INFRUA_PROJECT_ID=
```
{% endtab %}
{% endtabs %}

## Prometheus

* [Prometheus](https://prometheus.io/download/)
  * Below is the config you can use to feed Yearn-Exporter into prometheus. This has to have exact spacing or it will throw an error. 

{% tabs %}
{% tab title="prometheus.yml" %}
```javascript
# my global config
global:
  scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
  - static_configs:
    - targets:
      # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: 'yearnv2'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
    - targets: ['localhost:8801']
  - job_name: 'yearn'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
    - targets: ['localhost:8800']  
  - job_name: 'prometheus'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
    - targets: ['localhost:9090']

```
{% endtab %}
{% endtabs %}

## Python

* Python

  * install from [https://www.python.org/downloads/](https://www.python.org/downloads/)

## Brownie

* Check if pip is installed via

```text
C:\> py -m pip --version
pip X.Y.Z from ...\site-packages\pip (python X.Y)
```

If it is not install pip from here [https://pip.pypa.io/en/stable/installing/](https://pip.pypa.io/en/stable/installing/) then

```text
pip install eth-brownie
```

## Etherscan API key

* Make an Etherscan account and [api key](https://etherscan.io/myapikey)
* Add `ETHERSCAN_TOKEN` as a variable in windows under user variables
  * you can either add it manually or alternatively you can run `set ETHERSCAN_TOKEN=yourtokenkey` in cmd
* Make its value your Api-Key Token

![](../../../.gitbook/assets/envirvari.jpg)

* [Grafana](https://grafana.com/get)
  * After installing go to settings &gt; Data Sources &gt; Add Data Source
  * Select Prometheus
    * URL:  http://yourIPv4address:9090
    * Access: Browser
    * Save and test! Make sure yearn exporter is running and prometheus is also running. If it is working it will show green. 
  * Import pre-made dashboards found [here](https://github.com/DarkGhost7/yearn-exporter-info/tree/master/Dashboards) by + \(create\) &gt; import &gt; upload json file

