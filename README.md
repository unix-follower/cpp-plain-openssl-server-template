# cpp-plain-openssl-server-template

Build and run it with:

```bash
cmake -S . -B build
cmake --build build --target plain_openssl_api_server -j4
./build/plain_openssl_api_server --host 127.0.0.1 --port 9446
```

Optional runtime settings:
- `CPP_PLAIN_HOST` and `CPP_PLAIN_PORT` override bind address and port
- `CPP_HOST` and `CPP_PORT` are also accepted
- `CPP_PLAIN_MODE` supports `thread-per-request`, `thread-pool`, `blocking`, and `nonblocking`
- `CPP_PLAIN_THREADS` sets worker count for `thread-pool` mode
- `SERVER_HOST`, `SERVER_PORT`, and `PORT` remain generic fallbacks
- `TLS_CERT_FILE`, `TLS_KEY_FILE`, and optional `TLS_KEY_PASSWORD` can be set explicitly

Verification:

```bash
curl -ik https://127.0.0.1:8443/api/health
curl -ik "https://127.0.0.1:8443/api/health?mode=error"
curl -ik https://127.0.0.1:8443/api/cid4/conformer/1
curl -ik https://127.0.0.1:8443/api/cid4/compound
```
