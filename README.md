

# Minecraft Forge Docker Configuration

This repository provides a Docker configuration for a Minecraft Forge 1.7.10 server. It includes the necessary installer jar and Minecraft server configuration files (ops.json, server.properties, etc.). This repository can be used as a base for your own custom server.

## Features
- Pre-configured Dockerfile for Minecraft Forge 1.7.10
- Includes necessary installer jar and Minecraft server configuration files
- Easy to customize for your own needs

## Getting Started

To get started, you will need to have Docker installed on your system. Once Docker is installed, you can clone this repository and run the following commands from the **docker** folder:

    docker-compose up -d

This will build the Docker image and start the Minecraft server. You can then connect to the server using your Minecraft client. The default server IP address is localhost and the default port is 25565.

## Customization

You can customize the server by modifying the **docker-compose.yml** and the **configuration files**. The docker-compose file defines the environment for the server, while the configuration files control the server settings.

### docker-compose.yml

The docker-compose.yml defines the following environment variables:

- **command** - Default command is `["java", "-Xms1G", "-Xmx2G", "-jar", "minecraft_server.jar", "nogui"]`. **-Xms** defines minimum amount of RAM it will be accumulated to Minecraft server. **-Xmx** defines maximum amount of RAM it will be accumulated to Minecraft server

### Configuration Files

The configuration files include the following:

- **ops.json**: This file defines the server operators.
- **server.properties:** This file controls the server settings.

## Contributing

We welcome contributions to this project. Please feel free to submit pull requests with your changes.

## License

This project is licensed under the GNU General Public License v3.0.
https://www.gnu.org/licenses/gpl-3.0.en.html
