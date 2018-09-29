<p align="center">
    <a href="https://webhookrelay.com" target="_blank"><img width="100"src="https://webhookrelay.com/images/sat_logo.png"></a>
</p>

# Hass.io Add-on: Webhook Relay

Reverse tunnels for your Home Assistant. 


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

Our free plan includes:

* One bidirectional tunnel suitable for remote access, due to the lack of HTTPS we wouldn't recommend using them from unsafe wifi networks.
* End-to-end encrypted webhooks forwarding (150 webhooks per month)

For most users "basic" plan ($4.50/month) should be enough, it includes:

* Custom subdomains
* HTTPS for bidirectional tunnel endpoints
* 3 tunnels (for example Home Assistant, Node-RED and anything else)
* 1500 webhooks per month

All plans can be viewed [here](https://webhookrelay.com/pricing/). Alternative ways to earn HTTPS and custom subdomains:

* Blog about it :) 
* Tweet about [@Webhook Relay](https://twitter.com/webhookrelay)
* Provide useful feedback

## Coming soon

* Custom domains through CNAME DNS entries, such as hass.yourdomain.com
* TLS pass-through without TLS termination on our side. This will allow Webhook Relay to relay traffic to your Home Assistant without terminating HTTPS. Combined with custom domains this feature will allow to create fully encrypted tunnels so even if we wanted, we couldn't spy on your traffic. It might require a bit more work on your end to setup TLS termination with NGINX or similar tools though. 