# Hass.io Add-on: Webhook Relay

Secure and fast reverse tunnels for your Home Assistant.

<p align="center">
    <a href="https://webhookrelay.com/v1/guide/home-automation.html#Home-Assistant" target="_blank"><img src="https://webhookrelay.com/images/hassio-addon.jpeg"></a>
</p>

# Docker Status

![Supports armhf Architecture][armhf-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

[![Docker Layers][layers-shield]][microbadger]
[![Docker Pulls][pulls-shield]][dockerhub]


[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[layers-shield]: https://images.microbadger.com/badges/image/webhookrelay/webhookrelayd.svg
[pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/jupyterlablite.svg
[microbadger]: https://microbadger.com/images/webhookrelay/webhookrelay
[dockerhub]: https://hub.docker.com/r/webhookrelay/webhookrelayd

Using `webhookrelayd` version `1.9.0`

# About

Webhook Relay works by opening a connection to the public cloud service and giving you your unique "webhooks inbox" URL or your own domain/subdomain which you can supply to 3rd party services.

Webhook Relay is particularly useful when:

* You cannot access your router to configure port forwarding
* Router doesn't support port forwarding
* Your ISP blocks inbound connections
* You don't have a static IP address
* Server that is hosting your home automation system is changing IP, location

## Installation

Installation instructions can be found [here](https://webhookrelay.com/v1/installation/home-assistant)

## Plans and pricing

Webhook Relay is a hosted service that requires infrastructure, support and development time. Our business model is providing a service for a fee. We do not share any of your data with 3rd parties (except Stripe for billing purposes). We recommend several plans:

* **Basic** plan that includes HTTPS and TLS tunnels - $4.5/month (works with DuckDNS)
* **Basic Plus** plan that includes HTTPS, TLS tunnels + whitelabel domains - $9.99/month

More plans available. If you are a service provider or want to provide Webhook Relay to a group of people. We can provide a self-hosted server version.

## Getting help

Most issues can be solved following the [installation](https://webhookrelay.com/v1/installation/home-assistant) instructions. Check whether you set a correct domain name and destination IP address. Examples include http://127.0.0.1:8123 where 127.0.0.1 is a special IP address that your operating system routes locally, don't replace it with actual IP address of your machine. 

If you can't resolve your issue, contact as at info@webhookrelay.com

## New in 2.2.0 version

We have added [Cloudflare](https://www.cloudflare.com/) integration to provide secure TLS pass-through tunnels for any domains (not just DuckDNS anymore). You can transfer your domain management to Cloudflare (it's free) and then use this add-on to create tunnels and automatically configure HTTPS. To start using Cloudflare, set `provider` field in the tunnel:

```json
"tunnels": [
		{
			"name": "cf-domain", 
			"destination": "http://127.0.0.1:8123",
			"protocol": "tls",			
			"domain": "ha.example.com",
			"provider": "cloudflare"
        }        
	],
```

And add Cloudflare email and API key:

```json
	"cloudflare": {
		"email": "your-email@example.com",
		"api_key": "your-token"
	},
```