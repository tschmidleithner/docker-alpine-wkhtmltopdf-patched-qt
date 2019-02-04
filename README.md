#### Alpine Linux 3.8 wkhtmltopdf 0.12.5-dev (with patched qt)

Based on [alloylab/Docker-Alpine-wkhtmltopdf](https://github.com/alloylab/Docker-Alpine-wkhtmltopdf)

Alpine has wkhtmltopdf package but with unpatched qt, therefor not all wkhtmltopdf features can be used. 

This container aim to build wkhtmltopdf and patched qt.

Resulting binary from build process can be reused as long as glib and openssl packages is installed.

Build step:

```
docker build -t aantonw/wkhtmltohtml .
docker run --name wkhtmltopdf -it aantonw/wkhtmltopdf html
```
