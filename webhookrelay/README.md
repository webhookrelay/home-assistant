# Hass.io Add-on: Webhook Relay

Secure and fast reverse tunnels for your Home Assistant.

<p align="center">
    <a href="https://webhookrelay.com/v1/guide/home-automation.html#Home-Assistant" target="_blank"><img src="https://webhookrelay.com/images/hassio-addon.jpeg"></a>
</p>

# About

Webhook Relay addon enables Home Assistant and any other services running inside internal network to receive webhooks from public services such as [IFTTT](https://ifttt.com), [Zapier](https://zapier.com/), Mailgun or pretty much anything.

It works by opening a connection to the public cloud service and giving you your unique "webhooks inbox" URL which you can supply to 3rd party services.

Webhook Relay is particularly useful when:

* You cannot access your router to configure port forwarding
* Router doesn't support port forwarding
* Your ISP blocks inbound connections
* You don't have a static IP address
* Server that is hosting your home automation system is changing IP, location

## Quick Start

Before starting the add-on, sign up [here](https://my.webhookrelay.com).

Installation of this add-on is pretty straightforward and not different in comparison to installing any other [Hass.io](https://hass.io) add-on:

  1. Add our Hass.io add-ons repository URL to your Hass.io instance: https://github.com/webhookrelay/home-assistant (If you are seeing this through your Home Assistant add-ons page, skip it)
  2. Install the “Webhook Relay” add-on.
  3. Generate [token key & secret pair](https://my.webhookrelay.com/tokens) and add it to the add-on's configuration 
  4. Start the “Webhook Relay” add-on.
  5. Check the logs of the “Webhook Relay” add-on to see if everything went well. It should print out your public URL.

Detailed instructions on how to set it up can be found here https://webhookrelay.com/v1/guide/home-automation.html. 

## Plans and Pricing

Webhook Relay is a hosted service that requires infrastructure, support and development time. Our business model is providing a service for a fee. We do not share any of your data with 3rd parties (except Stripe for billing purposes).

**Our free plan includes:**

* One bidirectional tunnel suitable for remote access, due to the lack of HTTPS we wouldn't recommend using them from unsafe wifi networks.
* End-to-end encrypted webhooks forwarding (150 webhooks per month)

For most users **basic** plan (*$4.50/month*) will be enough, it includes:

* Custom subdomains
* HTTPS for bidirectional tunnel endpoints with TLS termination on Webhook Relay servers (less secure, more convenient)
* TLS pass-through tunnels for maximum security (make sure your Home Assistant can terminate TLS or supply key & certificate to the agent to do the termination)
* 3 tunnels (for example Home Assistant, Node-RED and anything else)
* 1500 webhooks per month

**Basic Plus** plan includes **basic** plan features with an addition on whitelabel domains, such as hass.yourdomain.com.

All plans can be viewed [here](https://webhookrelay.com/pricing/). Alternative ways to earn HTTPS and custom subdomains:

* Blog about it :) 
* Tweet about [@Webhook Relay](https://twitter.com/webhookrelay)
* Provide useful feedback


## Configuration examples

TLS pass-through tunnel with Home Assistant decrypting/encrypting traffic and webhook forwarding rule:

```javascript
{
	"key": "your-key",
	"secret": "your-secret",
	"forwarding": [
	  {
		  "bucket": "my-ifttt",
		  "destination": "https://bin.webhookrelay.com/v1/webhooks/7d509cd1-c9aa-48db-ad4d-6a750ee2ggg"
	  }
	],
	"tunnels": [
		{
			"name": "customdomain",                   // optional tunnel name
			"subdomain": "",                          // optional subdomain
      "domain": "ha.keel.sh",                   // optional domain (requires whitelisted domains feature)
			"destination": "https://127.0.0.1:8123",  // Home Assistant address
			"protocol": "tls",                        // pick between tls/http/https 
			"cert_file": "",                          // not set, Home Assistant will terminate TLS
			"key_file": "",			                      // not set, Home Assistant will terminate TLS
			"auto_gen": false

		}
	],
	"tunnels_enabled": true,
	"forwarding_enabled": true
}

```

TLS pass-through tunnel with auto-generated, self-signed certificates from the agent. Home Assistant running simple HTTP. Traffic is encrypted end-to-end and only decrypted on localhost:

```javascript
{
	"key": "your-key",
	"secret": "your-secret",
	"forwarding": [
	  {
		  "bucket": "my-ifttt",
		  "destination": "https://bin.webhookrelay.com/v1/webhooks/7d509cd1-c9aa-48db-ad4d-6a750ee2ggg"
	  }
	],
	"tunnels": [
		{
			"name": "customdomain",                   // optional tunnel name
			"subdomain": "",                          // optional subdomain
      "domain": "ha.keel.sh",                   // optional domain (requires whitelisted domains feature)
			"destination": "https://127.0.0.1:8123",  // Home Assistant address
			"protocol": "tls",                        // pick between tls/http/https 
			"cert_file": "tls.crt",                   // TLS certificate
			"key_file": "tls.key",			              // TLS private key
			"auto_gen": true                          // Auto-generate key & cert if doesn't exist

		}
	],
	"tunnels_enabled": true,
	"forwarding_enabled": true
}

```