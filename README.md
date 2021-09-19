# Deployment of Guardian Bot to Heroku

This repository demonstrates the utilisation of [Guardian](https://github.com/open-web3-stack/guardian) to automatically deploy created with Guardian bot to Heroku.

As an example, we used the DeX Price bot that spots all price changes in the selected pair after each trade in Karura DeX. This Example can be upgraded to Arbitrage Bot Between Karura DeX and another exchange. You can read more about it [here](https://github.com/open-web3-stack/guardian/tree/master/packages/example-guardian#dex-price-guardian-bot-for-acalakarura).

This code utilises `@open-web3/example-guardian` library that contains some of the examples where guardian can be used.

Each of the bot's examples includes environment variables you need to setup. To automatically pass them to Heroku you can alter `app.json`:
```json=
{
...,
"env": {
    "NODE_ENDPOINT": {
      "description": "WebSocket node endpoint to connect",
      "value": "wss://mandala6.laminar.codes/"
    },
    "TOKEN_A": {
      "description": "TOKEN_A",
      "value": "DOT"
    },
    "TOKEN_B": {
      "description": "TOKEN_A",
      "value": "AUSD"
    }
  }
}
```

Heroku will run command in `Procfile`:
```bash=
node index.js & yarn collateral-auction
```

This code will run a simple HTTP server to display that code ran without errors and besides it will run a bot.

To deploy code to Heroku with current settings you can use the button below:

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/AcalaNetwork/collateral-auction-bot-template)


After clicking `Deploy` you will be presented with default parameters for DeX Price Bot:

![](https://i.imgur.com/f8BK02X.png)

After clicking `Deploy app` in Heroku in the interface the app will install dependencies and run the HTTP server along with DeX Price bot. The web interface of the UI should display the text `It's running...`

### Another Examples

You can find the list of supported examples here:
[package.json:bin](https://github.com/open-web3-stack/guardian/blob/a6fc3967b1a9568c3d9cc4f84324ffe047b95b1d/packages/example-guardian/package.json#L7)

> Note: :warning: that some of the examples will require more memory usage, and you may need to upgrade your Heroku container.