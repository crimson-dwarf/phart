# phart

You meant `php artisan`. We all have those days. 💨

This is two lines of bash in a trench coat. It is not a Laravel package. It will not be on Packagist. That would be silly.

## If you run Laravel in Docker

Put `phart` in your image build context (next to the Dockerfile, or e.g. `docker/phart`), paste [`docker.snippet`](docker.snippet) into your **app/php** Dockerfile, and rebuild.

```bash
docker compose exec app phart migrate
docker compose exec app phart test
```

BuildKit (default in recent Docker):

```dockerfile
COPY --chmod=755 phart /usr/local/bin/phart
```

Older Docker, two lines:

```dockerfile
COPY phart /usr/local/bin/phart
RUN chmod +x /usr/local/bin/phart
```

## If you run it on WSL

```bash
cp phart ~/.local/bin/phart && chmod +x ~/.local/bin/phart
```

`~/.local/bin` is usually on `PATH`. No sudo required.

## Usage

```bash
phart migrate
phart queue:restart
phart test
```

Same arguments and exit code as `php artisan`. Run it from the Laravel project root, like you would anyway.
