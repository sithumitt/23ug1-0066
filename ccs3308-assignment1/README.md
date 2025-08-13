# CCS3308 - Assignment 1: Virtualization and Containers

## Deployment Requirements
- Docker Engine
- Docker Compose (plugin)  
- Ubuntu VM (VMware)

## Application Description
Two-service Docker app:
- **web (Flask)** on port **5000**
- **db (MySQL 8.0)** on port **3306**, with persistent named volume **db-data**

## Network and Volume
- Network: **app-net** (Docker bridge network)
- Volume: **db-data** (named, persists MySQL data)

## Container Configuration
- **web**: built from `web/Dockerfile`, uses env vars to connect to `db`
- **db**: `mysql:8.0` image, initialized with database `mydb`

## How to Use
```bash
# Create application resources
./prepare-app.sh

# Run the application
./start-app.sh
# The app is available at http://localhost:5000

# Pause the application (preserves data)
./stop-app.sh

# Delete all application resources (containers, images, network, volume)
./remove-app.sh




