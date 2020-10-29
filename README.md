# Hjemmeserver

## Description

This is a docker-compose repo based on:

- [Docker Media Server with Traefik 2 Reverse Proxy](https://www.smarthomebeginner.com/traefik-2-docker-tutorial/)
- [WordPress on Docker with Nginx, Traefik, LE SSL, Security, and Speed](https://www.smarthomebeginner.com/wordpress-on-docker-traefik/)
- [Synology Docker Media Server with Traefik, Docker Compose, and Cloudflare](https://www.smarthomebeginner.com/synology-docker-media-server/)

<strong>Supporting Articles:</strong>

- [Cloudflare Settings for Traefik Docker: DDNS, CNAMEs, & Tweaks](https://www.smarthomebeginner.com/cloudflare-settings-for-traefik-docker/)
- [Google OAuth 2 MFA Protection for Docker](https://www.smarthomebeginner.com/google-oauth-with-traefik-docker/)
- [Authelia MFA Protection for Docker](https://www.smarthomebeginner.com/docker-authelia-tutorial/)
- [Traefik Docker Security Best Practices](https://www.smarthomebeginner.com/traefik-docker-security-best-practices/)


# Usage

## Installation

First, install Docker and Docker Compose, as described in our <a href="https://www.smarthomebeginner.com/docker-home-media-server-2018-basic/">Docker Media Server guide</a>.

1. Clone the repo.
2. Configure `traefik.toml`

- Rename `traefik\traefik.toml.example` to `traefik\traefik.toml`
- Edit it to reflect your situation
- Edit domain name.
- DNS Challenge (for LetsEncrypt verification) is enabled by default for cloudflare. Use the [Traefik Reverse Proxy guide](https://www.smarthomebeginner.com/traefik-reverse-proxy-tutorial-for-docker/) for help with this.
- For other providers other than cloudflare, [check here](https://docs.traefik.io/v2.0/https/acme/#providers).

3. (Optional) Enable or use HTTP Basic Authentication by renaming `shared\.htpasswd.example` to `shared\.htpasswd` in the folder and adding username and hashed password to it.
4. Configure environmental variables (`.env` file)

- Rename the included `.env.example` to `.env`.
- Edit variables in `.env` file.
- All variables (ie. `${XXX}`) in docker-compose.yml come from `.env` file stored in the same place as docker-compose.yml.
- Ensure good permissions for the `.env` file (recommended: 640).

5. Edit `docker-compose.yml` to include only the services you want or add additional services to it. Be sure to read the comments for each app and create any required files.
6. Start and stop your docker stack as described in our [Docker Media Server guide](https://www.smarthomebeginner.com/docker-home-media-server-2018-basic/).
7. (Optional) Put non-docker apps behind Traefik proxy by renaming `traefik\rules\app.toml.example` to `traefik\rules\app.toml` and editing its contents.

## Starting and Stopping

I use bash_aliases to simplify starting and stopping containers/stack. Included in the repo is an example of bash_aliases I use (replace USER with your Linux username). Here are some example alias commands:

- <strong>dc1up</strong> or <strong>dc2up</strong> - Create network and start Docker Traefik 1 or 2 stack
- <strong>dc1down</strong> or <strong>dc2down</strong> - Stop Docker Traefik 1 or 2 stack
- <strong>dcup1</strong> or <strong>dcup2</strong> - Start Docker Traefik 1 or 2 stack
- <strong>dcup1v</strong> or <strong>dcup2v</strong> - Start Docker Trafik 1 or 2 VPN stack
- <strong>dcdown1</strong> or <strong>dcdown2</strong> - Stop Docker Traefik 1 or 2 stack
- <strong>dcdown1v</strong> or <strong>dcdown2v</strong> - Stop Docker Traefik 1 or 2 VPN stack
- <strong>dcrec1</strong> or <strong>dcrec2</strong> - Start or recreate a specific service
- <strong>dcstop1</strong> or <strong>dcstop2</strong> - Stop a specific service
- <strong>dcrestart1</strong> or <strong>dcrestart2</strong> - Restart a specific service
- <strong>dclogs1</strong> or <strong>dclogs1v</strong> or <strong>dclogs2</strong> or <strong>dclogs2v</strong> - See real-time logs for the corresponding stack or service
- <strong>dcpull1</strong> or <strong>dcpull1v</strong> or <strong>dcpull2</strong> or <strong>dcpull2v</strong> - Pull new images for the corresponding stack or service

## Did this Repo help you?

Please consider buying the original author a coffee (or two) as a token of appreciation.

<a href="https://www.buymeacoffee.com/smarthomebeginr" target="_blank" rel="nofollow noopener noreferrer"><img src="https://www.smarthomebeginner.com/images/2020/04/coffee.png" alt="" width="340" height="77" class="aligncenter size-full wp-image-41005" /></a>
