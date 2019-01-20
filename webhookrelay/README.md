# Hass.io Add-on: Webhook Relay

Secure and fast reverse tunnels for your Home Assistant.

<p align="center">
    <a href="https://webhookrelay.com/v1/guide/home-automation.html#Home-Assistant" target="_blank"><img src="https://webhookrelay.com/images/hassio-addon.jpeg"></a>
</p>

# About

Webhook Relay works by opening a connection to the public cloud service and giving you your unique "webhooks inbox" URL or your own subdomain which you can supply to 3rd party services.

Webhook Relay is particularly useful when:

* You cannot access your router to configure port forwarding
* Router doesn't support port forwarding
* Your ISP blocks inbound connections
* You don't have a static IP address
* Server that is hosting your home automation system is changing IP, location

## Quick Start - TLS pass-through tunnel

Before starting the add-on:

* Sign up [here](https://my.webhookrelay.com)
* Get [DuckDNS](https://www.duckdns.org/) account (optional, although recommended)
* Make sure your Home Assistant can terminate TLS, otherwise our add-on can do TLS termination but it will generate a self-signed one or you can supply your own certs to it

Installation of this add-on is pretty straightforward and not different in comparison to installing any other [Hass.io](https://hass.io) add-on:

  1. Add our Hass.io add-ons repository URL to your Hass.io instance: https://github.com/webhookrelay/home-assistant (If you are seeing this through your Home Assistant add-ons page, skip it)
  2. Install the “Webhook Relay” add-on.
  3. Generate [token key & secret pair](https://my.webhookrelay.com/tokens) and add it to the add-on's configuration.
  4. Get [DuckDNS](https://www.duckdns.org/) token and create your domain. Add those details to the "tunnels" config section and "duck_dns" section. Set "accept_terms" to true if you accept [Let's Encrypt ToS](https://community.letsencrypt.org/tos).
  6. Start the “Webhook Relay” add-on.  
  7. Check the logs of the “Webhook Relay” add-on to see if everything went well. It should print out your public URL.

Detailed instructions on how to set it up can be found here https://webhookrelay.com/v1/guide/home-automation.html.

## Plans and Pricing

Webhook Relay is a hosted service that requires infrastructure, support and development time. Our business model is providing a service for a fee. We do not share any of your data with 3rd parties (except Stripe for billing purposes). We recommend several plans:

* **Free** plan includes 150 webhooks per month and one HTTP tunnel
* **Basic** plan that includes HTTPS and TLS tunnels - $4.5/month

## TLS pass-through config example

```json
{
	"key": "[YOUR TOKEN KEY]",
	"secret": "[YOUR TOKEN SECRET]",
	"forwarding": [],
	"tunnels": [
		{
			"name": "ha",
			"destination": "http://127.0.0.1:8123",
			"protocol": "tls",			
			"domain": "[YOUR DUCKDNS HA DOMAIN].duckdns.org"			
		},
		{
			"name": "node-red",
			"destination": "http://127.0.0.1:1880",
			"protocol": "tls",			
			"domain": "[YOUR DUCKDNS NODERED DOMAIN].duckdns.org"			
		}
	],
	"duck_dns": {
		"token": "[YOUR DUCKDNS TOKEN]",
		"accept_terms": true
	},
	"tunnels_enabled": true,
	"forwarding_enabled": false
}
```