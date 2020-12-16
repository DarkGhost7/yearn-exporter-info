# Running Everything

After installing Python, Prometheus, Grafana, and downloading Yearn-Exporter. 

## Yearn-Exporter

If you haven't already downloaded yearn exporter, install [git](https://git-scm.com/download/win), then find a place where you would like to put the exporter. In the address bar of that folder type cmd to open command prompt then type

```text
git clone https://github.com/iearn-finance/yearn-exporter
cd yearn-exporter
brownie run yearn exporter_v1 --network mainnet
```

Now your v1 exporter should be running. Open another command prompt in the yearn-exporter folder via the trick above and run

```text
brownie run yearn exporter_v2 --network mainnet
```

Now both v1 and v2 exporter should be running. 

## Prometheus

Find where Prometheus is installed at probably somewhere like the below directory

{% hint style="info" %}
C:\Users\YOURUSERNAMEHERE\Documents\Python\prometheus-2.22.1.windows-amd64
{% endhint %}

Once there best to run it prometheus from cmd to see any error/read them later. Open cmd anywhere then navigate to your prometheus install folder.

{% tabs %}
{% tab title="Command Prompt" %}
```text
cd C:\Users\YOURUSERNAMEHERE\Documents\Python\prometheus-2.22.1.windows-amd64
```
{% endtab %}
{% endtabs %}

Next run

```text
prometheus.exe
```

If you don't see any errors it should be up and running. You can check by visiting [http://localhost:9090/](http://localhost:9090/)

If you set up the config correctly and yearn exporter is running you should see all green here [http://localhost:9090/targets](http://localhost:9090/targets) 

## Grafana

Navigate to the directory where you installed grafana most likely

{% hint style="info" %}
C:\Program Files\GrafanaLabs\grafana
{% endhint %}

open command prompt here

```text
cd bin
grafana-server.exe
```

Now if everything we well grafana should be up and running at [http://localhost:3000/](http://localhost:3000/) it will ask you to make a new password and just do that then you should be good to go to make your own custom yearn dashboard or add the premade ones how it's shown [here](https://darkghost.gitbook.io/yearn-exporter-info/tips-for-installing)

