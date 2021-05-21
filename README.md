## monero-wallet-nats-publisher

Builds a Docker image with Monero Wallet RPC set up to publish Monero Transactions to a NATS Streaming server, using the `--tx-notify` param to invoke a CLI util (https://github.com/xmrstuff/monero-nats-publisher)

The image is built and published to https://hub.docker.com/repository/docker/xmrstuff/monero-wallet-nats-publisher

### Configuration

The `CMD` included in the Dockerfile is an example that uses the default configuration of the CLI util. You'd need to overwrite the `CMD` to pass custom configuration. Something like:

```bash
/usr/bin/publisher ping && \
    /usr/bin/monero-wallet-rpc \
    --non-interactive \
    --tx-notiy="/usr/bin/publisher --nats-url=my-nats-server:422 tx %s"
```

See the README in the CLI's repo (https://github.com/xmrstuff/monero-nats-publisher) for more info 