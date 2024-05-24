# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM
#FROM ghcr.io/home-assistant/amd64-base-debian:bullseye

# LABEL io.hass.version="1.0" io.hass.type="addon" io.hass.arch="aarch64|amd64"

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH

RUN apt-get update && apt-get install -y \
    nodejs

RUN curl -s https://raw.githubusercontent.com/sbs20/scanservjs/master/bootstrap.sh | bash -s -- -v latest
#RUN curl -s https://github.com/sbs20/scanservjs/releases/download/v3.0.3/scanservjs_3.0.3-1_all.deb
#RUN apt-get install ./scanservjs_3.0.0-1.deb

# Copy root filesystem
COPY rootfs /

RUN chmod a+x /run.sh

CMD ["/run.sh"]

# RUN chmod a+x /entrypoint.sh
# RUN ["chmod", "+x", "/entrypoint.sh"]
# CMD [ "/entrypoint.sh" ]