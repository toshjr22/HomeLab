# Hosting Your Own Cloud Services

## How I Use My Current Setup

- **NGINX Proxy Manager**: Acts as a reverse proxy to route external traffic to internal services like NextCloud and Immich, managing SSL certificates and load balancing.
- **Cloudflare**: Handles DNS records for domain resolution and implements Zero Trust policies for secure, authenticated access to services without direct port exposure.
- **NextCloud**: Provides cloud storage, file synchronization, and collaboration tools, allowing access to files from multiple devices.
- **Immich**: Manages and organizes personal photos, offering features like facial recognition, albums, and sharing.
- **docker-icloudpd**: Runs as a Docker container to automatically download photos from iCloud and upload them to Immich, ensuring all iCloud photos are backed up and accessible in my self-hosted photo library.