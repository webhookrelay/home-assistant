ARG BUILD_FROM
FROM $BUILD_FROM
ENTRYPOINT ["/relayd", "--mode", "home-assistant"]

# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Webhook Relay" \
    io.hass.description="Receive webhooks without public IP or configuring NAT via your hass.io instance" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Karolis Rusenas <karolis@webhookrelay.com>" \
    org.label-schema.description="Receive webhooks without public IP or configuring NAT via your hass.io instance" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Webhook-Relay" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://webhookrelay.com/" \
    org.label-schema.usage="https://webhookrelay.com/v1/guide/home-automation.html#Home-Assistant" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/webhookrelay/home-assistant" \
    org.label-schema.vendor="Webhook Relay"