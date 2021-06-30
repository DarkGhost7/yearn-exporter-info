# Running via Docker

## Setting Environment Variables

Grafana Dashboard Variables

```
export GF_SECURITY_ADMIN_USER=<YOUR_ADMIN_USER>
```

Change this if you want to have a different admin user name, default is admin.



```text
export GF_SECURITY_ADMIN_PASSWORD=<YOUR_ADMIN_PASSWORD>
```

Change this if you want to have a different admin password, default is admin.

```text
export WEB3_INFURA_PROJECT_ID=<YOUR_PROJECT_ID>
```

**This needs to be set.** Generate an Ethereum project api key via [Infura.io](https://infura.io/). This is the Project ID key.

```text
export WEB3_PROVIDER=<YOUR_WEB3_PROVIDER>
```

If this is set, it overrides Infura, and instead a custom url is used as the web3 provider. This can be a url to a Ethereum Archive/Full Node.

```text
export ETHERSCAN_TOKEN=<YOUR_ETHERSCAN_TOKEN>
```

**This needs to be set.** Generate an Etherscan api key via [Etherscan.io](https://etherscan.io/).

```text
export SLEEP_SECONDS=<YOUR_SLEEP_SECONDS>
```

If this is set, the exporters will wait the given amount of time between subsequent invocations to your web3 provider. If you are not using a full node and using infura you will need to rate limit your calls via SLEEP\_SECONDS. 

You will need to download and have docker & docker-compose installed. 

To run use the follow command in the root directory of Yearn-Exporter. 

```text
docker-compose --file services/dashboard/docker-compose.yml --project-directory . up --build
```

After successful startup you can go directly to grafana at `http://localhost:3000`. If you want to change your dashboards you can sign-in at the lower left with `admin:admin .`

