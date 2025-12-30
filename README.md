# Home Lab Server Recipes

A collection of Docker-based server recipes and configurations for running various services in a home lab environment.

## Description

This repository contains Docker Compose configurations and related files for deploying self-hosted services. Each recipe is organized in its own subdirectory with all necessary configuration files, making it easy to deploy and manage services independently.

## Repository Structure

```
home-lab_server-recipes/
├── forticlient-tailscaled/    # FortiClient VPN + Tailscale subnet router
├── portainer-tailscaled/      # Portainer CE + Tailscale remote access
└── [future recipes...]
```

## Available Recipes

### 🔐 FortiClient-Tailscaled
Combines FortiClient VPN with Tailscale to create a subnet router, allowing access to VPN-protected networks through your Tailscale network.

**Use case**: Access corporate/private networks from anywhere via Tailscale without running VPN on each device.

### 🐳 Portainer-Tailscaled
Combines Portainer CE with Tailscale for secure, remote container management without exposing ports to the public internet.

**Use case**: Manage Docker containers from anywhere via Tailscale with a beautiful web UI.

## Getting Started

### Prerequisites
- Docker installed on your host machine
- Docker Compose (v2 recommended)
- Git with submodules support

### Clone the Repository

```bash
# Clone with submodules
git clone --recursive https://github.com/G-SLabs/home-lab_server-recipes.git

# Or if already cloned, initialize submodules
cd home-lab_server-recipes
git submodule update --init --recursive
```

### Deploy a Recipe

1. Navigate to the recipe directory:
```bash
cd forticlient-tailscaled
```

2. Copy the example configuration:
```bash
cp docker-compose.example.yml docker-compose.yml
```

3. Edit the configuration with your credentials:
```bash
nano docker-compose.yml
```

4. Start the service:
```bash
docker compose up -d
```

5. Check logs:
```bash
docker compose logs -f
```

## Tips & Tricks

### Managing Services

**Start all services:**
```bash
# From root directory
for dir in */; do (cd "$dir" && docker compose up -d); done
```

**Stop all services:**
```bash
for dir in */; do (cd "$dir" && docker compose down); done
```

**View logs for a specific service:**
```bash
cd <recipe-name>
docker compose logs -f [service-name]
```

### Updating Recipes

Since recipes may use git submodules:

```bash
# Update all submodules to latest commit
git submodule update --remote --merge

# Update a specific submodule
git submodule update --remote --merge forticlient-tailscaled
```

### Persistent Data

Most recipes store persistent data in local directories (volumes). Make sure to:
- Backup these directories regularly
- Set appropriate permissions (some services need specific UIDs/GIDs)
- Don't commit sensitive data to git (use .gitignore)

### Security Best Practices

1. **Never commit credentials** - Use environment files and add them to .gitignore
2. **Use secrets** - For sensitive data, consider Docker secrets or external secret management
3. **Keep images updated** - Regularly pull latest images for security patches
4. **Network isolation** - Use Docker networks to isolate services
5. **Restrict ports** - Only expose necessary ports to the host

### Troubleshooting

**Container won't start:**
```bash
docker compose logs [service-name]
docker compose ps
```

**Network issues:**
```bash
# Check if container can reach internet
docker compose exec [service-name] ping -c 4 8.8.8.8

# Check DNS resolution
docker compose exec [service-name] nslookup google.com
```

**Permission issues:**
```bash
# Check file ownership
ls -la

# Fix ownership (adjust UID:GID as needed)
sudo chown -R 1000:1000 ./volume-directory
```

**Clean up everything:**
```bash
# Stop and remove containers, networks, volumes
docker compose down -v

# Remove unused Docker resources
docker system prune -a
```

## Adding New Recipes

To add a new recipe to this repository:

1. Create a new directory for your recipe
2. Add a `docker-compose.yml` (or example file)
3. Include a README.md with specific instructions
4. Document required environment variables
5. Add example configurations
6. Test the deployment

### Recipe Structure Template

```
recipe-name/
├── README.md                    # Specific documentation
├── docker-compose.example.yml   # Example configuration
├── Dockerfile                   # Custom image (if needed)
├── .env.example                 # Environment variables template
└── config/                      # Configuration files
```

## Contributing

Contributions are welcome! If you have a useful home lab recipe:

1. Fork the repository
2. Create your recipe following the structure above
3. Test thoroughly
4. Submit a pull request with clear documentation

## License

Pattent Peding

## Support

For issues or questions:
- Open an issue on GitHub
- Check existing issues for solutions
- Review logs for error messages

---

**Happy Self-Hosting! (To myself I guess) 🏠🖥️**
