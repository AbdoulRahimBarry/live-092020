# Traefik

Traefik installation in kubernetes with LE support.

## Install traefik
```
k apply -f traefik.yaml
```

## Clean

```
k delete -f traefik.yaml
k delete -f app.yaml
```
