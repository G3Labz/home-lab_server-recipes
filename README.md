# Home Lab Server Recipes

A collection of Docker-based server recipes and configurations for running various services in a home lab environment.

## Description

This repository contains Docker Compose configurations and related files for deploying self-hosted services. Each recipe is organized in its own subdirectory with all necessary configuration files, making it easy to deploy and manage services independently.

## Repository Structure

```
home-lab_server-recipes/
├── arr-stack-tailscaled/         # *arr media automation stack + Tailscale
├── excalidraw-tailscaled/        # Excalidraw whiteboard + Tailscale
├── filebrowser-tailscaled/       # FileBrowser + Tailscale file management
├── forticlient-tailscaled/       # FortiClient VPN + Tailscale subnet router
├── gitea-tailscaled/             # Gitea + Act Runner + Tailscale CI/CD
├── it-tools-tailscaled/          # IT-Tools developer utilities + Tailscale
├── jellyfin-tailscaled/          # Jellyfin media server + Tailscale
├── librespeed-tailscaled/        # LibreSpeed speed test + Tailscale
├── pihole-tailscaled/            # Pi-hole + Unbound + Tailscale DNS server
├── portainer-tailscaled/         # Portainer CE + Tailscale remote access
├── rustdesk-tailscaled/          # RustDesk remote desktop + Tailscale
├── stremio_server-tailscaled/    # Stremio Server + Tailscale media streaming
└── [future recipes...]
```

## Available Recipes

### 🔐 FortiClient-Tailscaled
Combines FortiClient VPN with Tailscale to create a subnet router, allowing access to VPN-protected networks through your Tailscale network.

**Use case**: Access corporate/private networks from anywhere via Tailscale without running VPN on each device.

### 🐳 Portainer-Tailscaled
Combines Portainer CE with Tailscale for secure, remote container management without exposing ports to the public internet.

**Use case**: Manage Docker containers from anywhere via Tailscale with a beautiful web UI.

### 🛡️ Pi-hole-Tailscaled
Combines Pi-hole with Unbound (recursive DNS) and Tailscale for network-wide ad blocking accessible from anywhere through your Tailscale network.

**Features**:
- Network-wide ad blocking with Pi-hole
- Recursive DNS resolution with Unbound (no third-party DNS dependency)
- Secure access via Tailscale network
- Web-based admin interface

**Use case**: Block ads and trackers across all your devices via Tailscale DNS, with full privacy through recursive DNS resolution.

### 📺 Stremio-Server-Tailscaled
Combines Stremio Server (web player + streaming server) with Tailscale for secure, remote media streaming accessible from anywhere through your Tailscale network.

**Features**:
- Full Stremio web player and streaming server
- Built-in ffmpeg with hardware acceleration support (Intel/AMD VAAPI)
- Automatic server URL configuration
- Optional HTTPS with auto-generated certificates
- Optional HTTP Basic Authentication

**Use case**: Stream media from anywhere via Tailscale with Stremio's powerful addon ecosystem.

### 🛠️ IT-Tools-Tailscaled
Combines IT-Tools with Tailscale for secure access to 80+ developer utilities from anywhere on your Tailscale network.

**Features**:
- Encoders/decoders (Base64, JWT, URL, etc.)
- Converters (JSON, YAML, timestamps)
- Generators (UUID, hash, passwords)
- Network tools and calculators
- No tracking or analytics

**Use case**: Access a comprehensive toolkit of developer utilities securely from anywhere.

### 🏗️ Gitea-Tailscaled
Combines Gitea (self-hosted Git service) with Act Runner (CI/CD) and Tailscale for secure, remote Git and CI/CD management accessible from anywhere on your Tailscale network.

**Features**:
- Full Git server with web UI, issues, PRs, and releases
- GitHub Actions-compatible CI/CD with Act Runner
- Docker-based job execution for isolation
- SQLite database (no external dependencies)
- Secure access via Tailscale network

**Use case**: Host your own Git repositories and run CI/CD pipelines securely via Tailscale, without exposing to the public internet.

### 📁 FileBrowser-Tailscaled
Combines FileBrowser with Tailscale for secure, remote file management accessible from anywhere on your Tailscale network.

**Features**:
- Web-based file browser with upload/download
- User management with permissions
- File sharing capabilities
- Command execution support
- Dark theme available

**Use case**: Manage files on your server from anywhere with a beautiful web UI.

### 🎨 Excalidraw-Tailscaled
Combines Excalidraw with Tailscale for a self-hosted virtual whiteboard accessible from anywhere on your Tailscale network.

**Features**:
- Hand-drawn style diagrams and sketches
- Shapes, arrows, text, freehand drawing
- Export to PNG, SVG, clipboard
- No external tracking
- Works offline once loaded

**Use case**: Create beautiful diagrams and sketches with a privacy-focused whiteboard.

### 🚀 LibreSpeed-Tailscaled
Combines LibreSpeed with Tailscale for a self-hosted speed test server accessible from anywhere on your Tailscale network.

**Features**:
- Download/upload speed tests
- Ping and jitter measurements
- Optional telemetry/result storage
- No third-party dependencies
- Privacy-focused

**Use case**: Test network speeds across your Tailscale network without relying on external services.

### 🖥️ RustDesk-Tailscaled
Combines RustDesk Server with Tailscale for a self-hosted remote desktop solution accessible from anywhere on your Tailscale network.

**Features**:
- Cross-platform support (Windows, macOS, Linux, mobile)
- End-to-end encryption
- File transfer capabilities
- No account required for basic use
- Full control over infrastructure

**Use case**: Access your computers remotely with your own private remote desktop server.

### 🎬 Jellyfin-Tailscaled
Combines Jellyfin with Tailscale for a self-hosted media server accessible from anywhere on your Tailscale network.

**Features**:
- Movies, TV shows, music, live TV support
- Hardware transcoding (Intel QSV, NVIDIA, AMD)
- Multiple user accounts with parental controls
- Mobile and TV apps available
- Plugin ecosystem

**Use case**: Stream your media library from anywhere with a free, open-source media server.

### 📺 *arr-Stack-Tailscaled
Combines the popular *arr media automation applications with Tailscale for complete media library automation accessible from anywhere on your Tailscale network.

**Includes**:
- Prowlarr (indexer manager)
- Sonarr (TV shows)
- Radarr (movies)
- Lidarr (music)
- Readarr (books)
- Bazarr (subtitles)
- qBittorrent & SABnzbd (download clients)
- FlareSolverr (Cloudflare bypass)

**Use case**: Automate your entire media library management with industry-standard tools.

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

### Naming Conventions

Follow these naming patterns for consistency across all recipes:

**Recipe Directory Names:**
- Format: `<service>-tailscaled` (hyphen-separated, lowercase)
- Examples: `pihole-tailscaled`, `portainer-tailscaled`, `stremio_server-tailscaled`
- Use underscores only if the service name itself contains them (e.g., `stremio_server`)

**Data/Volume Directories:**
- Format: `<service>_data/` (underscore before `data`, lowercase)
- Examples: `pihole_data/`, `portainer_data/`, `stremio_data/`, `unbound_data/`
- Always use underscore (`_`) to separate service name from `data` suffix
- Never use hyphens in data directory names

**Tailscale State Directory:**
- Always use: `tailscale/state/`
- This pattern is shared across all recipes for consistency

**Configuration Files:**
- `docker-compose.yml` - Main compose file (gitignored, contains secrets)
- `docker-compose.example.yml` - Template without secrets (committed to git)
- `.env.example` - Environment variables template (if needed)

**Standard Directory Structure:**
```
recipe-name/
├── README.md                    # Specific documentation
├── docker-compose.example.yml   # Example configuration (no secrets)
├── docker-compose.yml           # Actual config (gitignored)
├── Dockerfile                   # Custom image (if needed)
├── .env.example                 # Environment variables template
├── <service>_data/              # Persistent data for main service
├── tailscale/                   # Tailscale configuration
│   └── state/                   # Tailscale state files
└── <other-service>_data/        # Data for additional services
```

### Adding a Recipe as a Submodule

If your recipe is in a separate Git repository, you can add it as a submodule:

```bash
# Add a new submodule
git submodule add https://github.com/username/recipe-repo.git recipe-name

# Commit the submodule addition
git add .gitmodules recipe-name
git commit -m "Add recipe-name as submodule"
```

**Converting an existing cloned repo to a submodule (recommended):**
```bash
# If you already have a cloned repo inside the workspace:
# 1. First, get the remote URL and recipe name
cd recipe-name
REPO_URL=$(git remote get-url origin)
RECIPE_NAME=${PWD##*/}

# 2. Move the repo out temporarily
cd ..
mv "$RECIPE_NAME" "../${RECIPE_NAME}-backup"

# 3. Add it as a proper submodule
git submodule add "$REPO_URL" "$RECIPE_NAME"

# 4. Copy any local changes/data if needed, then remove backup
cp -r "../${RECIPE_NAME}-backup/local-data" "$RECIPE_NAME/"  # if applicable
rm -rf "../${RECIPE_NAME}-backup"

# 5. Commit the submodule
git add .gitmodules "$RECIPE_NAME"
git commit -m "Add $RECIPE_NAME as submodule"
```

> **Note:** While there are "hacky" ways to convert a nested repo by editing `.gitmodules` directly,
> they often don't work reliably. The move-and-readd method above is the safest approach.

**Managing submodules:**
```bash
# Update a specific submodule to latest commit
git submodule update --remote --merge recipe-name

# Remove a submodule
git submodule deinit -f recipe-name
rm -rf .git/modules/recipe-name
git rm -f recipe-name
```

### Recipe Structure Template

```
recipe-name/
├── README.md                    # Specific documentation
├── docker-compose.example.yml   # Example configuration
├── Dockerfile                   # Custom image (if needed)
├── .env.example                 # Environment variables template
├── <service>_data/              # Persistent data (use underscore!)
├── tailscale/                   # Tailscale configuration
│   └── state/                   # Tailscale state files
└── config/                      # Additional configuration files
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
