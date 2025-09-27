# Nginx Notes and Recipes

This repository contains notes, configuration snippets, and example files for setting up and optimizing Nginx. The content is organized into the following folders:

- `Configuration/` — Common configuration snippets and examples for virtual hosts, location blocks, variables, rewrites, logging, PHP processing, worker tuning, timeouts, buffers, and dynamic modules.
- `installation/` — Basic installation notes and a minimal virtual host example for getting started.
- `Performace/` — Performance-related topics such as headers/expires, gzip compression, FastCGI cache, HTTP/2, and server push.
- `Security/` — Security hardening, HTTPS (SSL/TLS) configuration, rate limiting, and basic authentication examples.

Table of contents
- [Configuration](#configuration)
- [installation](#installation) 
- [Performace](#performace)
- [Security](#security)


## Configuration
Files in `Configuration/`:

- `01+Creating+a+Virtual+Host.conf` — Example virtual host server block for serving a site.
- `02+Location+Blocks.conf` — Examples of `location` block matching and best practices.
- `03+Variables.conf` — Notes on Nginx variables and how to use them.
- `04+Rewrites+&+Redirects.conf` — Common rewrite and redirect patterns using `rewrite` and `return`.
- `05+Try+Files+&+Named+Locations (1).conf` — `try_files` usage and named locations for cleaner routing.
- `06+Logging.conf` — Logging configuration including access_log and log_format examples.
- `07+Inheritince+&+Directive+Types (1).conf` — Explanation of inheritance rules and directive types across contexts.
- `08+PHP+Processing.conf` — FastCGI / PHP-FPM configuration examples.
- `09+Worker+Processes (1).conf` — Tuning `worker_processes`, `worker_connections`, and related directives.
- `10+Buffers+&+Timeouts.conf` — Buffer sizing, timeouts, and proxy/read/write timeout guidance.
- `11+Adding+Dynamic+Modules (1).conf` — Notes about building/adding dynamic modules to Nginx.
- `index.html`, `style.css`, `thumb.png` — Example static site assets used alongside the snippets.

Tips:
- Use `include` to compose reusable snippets into full server blocks.
- Validate configs with `nginx -t` before reloading.


## installation
Files in `installation/`:

- `01+Creating+a+Virtual+Host.conf` — Minimal server block useful during initial setup.
- `index.html`, `style.css`, `thumb.png` — Example static files to verify the virtual host serves content.

Quick start:
1. Install Nginx using your platform package manager.
2. Place the virtual host file in `/etc/nginx/sites-available/` and symlink to `/etc/nginx/sites-enabled/` on Debian-based systems.
3. Test and reload: `nginx -t && systemctl reload nginx`.


## Performace
Files in `Performace/`:

- `12+Headers+&+Expires.conf` — Caching headers and expires directives to improve client caching.
- `13+Compressed+Responses+with+gzip.conf` — Gzip configuration for compressing responses.
- `14+FastCGI+Cache.conf` — FastCGI caching setup for PHP/backend acceleration.
- `15+HTTP2.conf` — Enabling HTTP/2 for improved multiplexing.
- `16+Server+Push.conf` — Example of HTTP/2 server push usage.

Performance tips:
- Enable gzip and tune `gzip_types` to match your assets.
- Use `expires` and `cache-control` for static assets and a proper cache-busting strategy.
- Consider `fastcgi_cache` for dynamic backends where caching is safe.


## Security
Files in `Security/`:

- `17+HTTPS+(SSL).conf` — TLS configuration examples, recommended ciphers, and certificate setup notes.
- `18+Rate+Limiting.conf` — `limit_req` and `limit_conn` examples to mitigate abuse.
- `19+Basic+Auth.conf` — Basic auth configuration for protecting staging or admin areas.
- `20+Hardening+Nginx.conf` — General hardening recommendations (headers, server_tokens, limits).

Security tips:
- Use Modern TLS settings (e.g., TLSv1.2+/strong ciphers) and automate renewals with Let's Encrypt.
- Keep `server_tokens off;` and limit exposed information in error pages.
- Combine rate limiting with firewall rules for robust protection.


## Contributing
If you have improvements or additional snippets, please open a PR with a short description of the change and which file it updates.


## License
This repository is provided as-is for educational purposes. No explicit license included.

