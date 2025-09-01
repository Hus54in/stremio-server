# Stremio Server
This project provides a Dockerized Stremio server that makes it possible to run Stremio on a local Linux server and access it from devices on your local network.

Normally, the [official Stremio iOS app](https://apps.apple.com/us/app/stremio-lite/id6741710156) only works as an organizer (it lets you browse and manage your library, but it cannot actually play videos). With this setup, the iOS app can connect to the local Stremio server and stream videos directly to iPhone or iPad.

This Stremio Server is build upon [Stremio/server-docker](https://github.com/Stremio/server-docker) and extends it by adding [alpine/mkcert](https://github.com/alpine-docker/multi-arch-docker-images) and [alpine/nginx](https://github.com/nginx/docker-nginx) to provide HTTPS on the local network so [Stremio Web](https://web.stremio.com/) (which requires HTTPS and offers a mobile-friendly UI and external-player support) can connect to the server while keeping server-side resource usage low.

This single-file docker-compose project wraps the official Stremio server image, automates local TLS certificate creation with mkcert, and configures nginx as a reverse proxy to serve the server over HTTPS on the LAN. That enables Stremio Web to access the server (Stremio Web blocks plain HTTP), use its mobile-friendly UI, and play videos in external players—reducing CPU and memory load on the server.

## Linux (using Docker) 
1. Follow the [setup](https://docs.docker.com/engine/install) guide for your linux distribution.

2. Download the `docker-compose.yml` onto your server using: 
`wget `

3. Run it using:
`docker compose up -d`

## OpenMediaVault 

1. Follow the Docker Compose for OMV [instructions](https://wiki.omv-extras.org/doku.php?id=omv6:omv6_plugins:docker_compose)
2. Create a file using the docker compose for omv. Add a name and paste the contents of [docker-compose.yml]() in the file section.
3. Save the file and click the up arrow icon (up button).

## Stremio on IOS/Ipad OS
1. Open Safari (other browers will not work), then go to `https://<your-server-url>` (make sure its HTTPS and not http) replace `<your-server-url>` with your server's url.
2. You will get "This Connection is Not Private" error. Click on "visit this website", and reload the website.
3. Go to [web.stremio.com](https://web.stremio.com) and login. Then profile > Settings > Streaming. Click on "+ Add URL" and add the same URL `https://<your-server-url>` you added before then select the URL again and copy the "Remote URL". 
4. Tap on share icon and select "Add to Home Screen".
5. Open the Stremio from Home Screen, Login and go to profile > Settings > Streaming. Click on "+ Add URL" and add paste the "Remote URL" you copied before.








