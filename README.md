# harmonia

## Build

### Whole application

```
nix-shell --run cargo b
```

### C Library Wrapper around libnixstore

```
nix-shell --run make
```

Note: The makefile is only to provide a way to build the c Library so it can be
used outside of rust as well.

## Configuration

Default values

```
bind = "127.0.0.1:8080"
workers = 4
max_connection_rate = 256
priority = 30
```

Per default we wont sign any narinfo because we don't have a secret key, to
enable this feature enable it by providing a path to a private key generated by
`nix-store --generate-binary-cache-key cache.example.com-1 /etc/nix/cache.sk /etc/nix/cache.pk`

```
sign_key_path = "/run/secrets/key"
```

Logging can be configured with
[env_logger](https://docs.rs/env_logger/latest/env_logger/). The default value
is `debug,actix_web=debug`. To only log errors use the following
`RUST_LOG=error` and to only disable access logging, use
`RUST_LOG=info,actix_web::middleware=error`


## Inspiration

- [eris](https://github.com/thoughtpolice/eris)
