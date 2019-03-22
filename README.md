#### Alpine Linux 3.8/3.9 wkhtmltopdf 0.12.5 (with patched qt)

Based on [alloylab/Docker-Alpine-wkhtmltopdf](https://github.com/alloylab/Docker-Alpine-wkhtmltopdf)

Alpine has wkhtmltopdf package but with unpatched qt, therefor not all wkhtmltopdf features can be used. 

This container builds wkhtmltopdf and patched qt.

Build step (Alpine 3.8):

```
# build the binary
docker build -t movio/wkhtmltopdf:latest .
# create a container
docker run --name wkhtmltopdf -it movio/wkhtmltopdf:latest pwd
# extract binary from container to host
docker cp wkhtmltopdf:/bin/wkhtmltopdf ./wkhtmltopdf
```

Usage (Alpine 3.9):

```
# install unpatched wkhtmltopdf via package manager to get all dependencies, and add some true type fonts
RUN apk add --no-cache \
    wkhtmltopdf=0.12.5-r0 \
    ttf-dejavu ttf-droid ttf-freefont ttf-liberation ttf-ubuntu-font-family

# patch the binary
COPY wkhtmltopdf /usr/bin/wkhtmltopdf

# add openssl dependencies
RUN echo 'http://dl-cdn.alpinelinux.org/alpine/v3.8/main' >> /etc/apk/repositories && \
    apk add --no-cache libcrypto1.0 libssl1.0 && \
    chmod +x /usr/bin/wkhtmltopdf && \
    /usr/bin/wkhtmltopdf --version
```
