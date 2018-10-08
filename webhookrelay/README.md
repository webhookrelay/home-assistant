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

Before starting the add-on:

* Sign up [here](https://my.webhookrelay.com).
* Make sure your Home Assistant can terminate TLS, otherwise our add-on can do TLS termination but it will generate a self-signed one or you can supply your own certs to it.

Installation of this add-on is pretty straightforward and not different in comparison to installing any other [Hass.io](https://hass.io) add-on:

  1. Add our Hass.io add-ons repository URL to your Hass.io instance: https://github.com/webhookrelay/home-assistant (If you are seeing this through your Home Assistant add-ons page, skip it)
  2. Install the “Webhook Relay” add-on.
  3. Generate [token key & secret pair](https://my.webhookrelay.com/tokens) and add it to the add-on's configuration   
  5. Start the “Webhook Relay” add-on.  
  6. Check the logs of the “Webhook Relay” add-on to see if everything went well. It should print out your public URL.

Detailed instructions on how to set it up can be found here https://webhookrelay.com/v1/guide/home-automation.html. 

## Plans and Pricing

Webhook Relay is a hosted service that requires infrastructure, support and development time. Our business model is providing a service for a fee. We do not share any of your data with 3rd parties (except Stripe for billing purposes). We recommend several plans:

* **Basic** plan that includes HTTPS and TLS tunnels - $4.5/month
* **Basic Plus** plan that includes HTTPS, TLS tunnels + whitelabel domains - $9.99/month
