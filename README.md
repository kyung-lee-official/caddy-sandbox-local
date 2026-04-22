# Caddy + mkcert Self-Signed Certificate Configuration

## mkcert

For Windows, you can install mkcert using winget:

```bash
winget install FiloSottile.mkcert
```

After installation, run this ONCE as Administrator to install the trusted root CA (fixes browser "not secure"):

```bash
mkcert -install
```

Then create your wildcard cert (for `*.sandbox.local`):

```bash
mkcert "*.sandbox.local"
```

## Caddy Configuration

In your Caddyfile, you can specify the paths to the generated certificate and key:

```caddy
next.sandbox.local {
	tls /path/to/your/cert.pem /path/to/your/key.pem
	# Other Caddy directives...
}
```

## Note

If you modified the certificate or key file, make sure to restart Caddy to apply the changes. Also to restart browsers to clear any cached certificate errors.
