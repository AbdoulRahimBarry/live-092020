# Traefik

## Download traefik

```
curl -L https://github.com/containous/traefik/releases/download/v2.3.0-rc4/traefik_v2.3.0-rc4_darwin_amd64.tar.gz | tar xzf -
```

## Check the traefik version
```bash
./traefik version
```

## Start traefik

```bash
./traefik --entrypoints.web.address=:80 \
    --api.insecure
```

Dashboard: http://127.0.0.1:8080

## Expose applications

```bash
docker run --rm -tid --name=whoami1 -p8081:80 containous/traefikee-webapp-demo:v2
docker run --rm -tid --name=whoami2 -p8082:80 containous/traefikee-webapp-demo:v2
docker run --rm -tid --name=whoami3 -p8083:80 containous/traefikee-webapp-demo:v2
```

## Dynamic configuration

```bash
./traefik --entrypoints.web.address=:80 \
    --api.insecure \
    --providers.file.filename=./dynamic.toml
```

Dashboard: http://127.0.0.1:8080

## Start with pilot

```bash
./traefik --entrypoints.web.address=:80 \
    --api.insecure \
    --providers.file.filename=./dynamic.toml \
    --experimental.pilot.token=XXXXX
```

## Start with rewrite body
```bash
./traefik --entrypoints.web.address=:80 \
    --api.insecure \
    --providers.file.filename=./dynamic.toml \
    --experimental.pilot.token=XXXXX \
    --experimental.plugins.rewritebody.modulename="github.com/containous/plugin-rewritebody" \
    --experimental.plugins.rewritebody.version="v0.2.2"
```
