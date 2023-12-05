# Base image for Minecraft Forge server
FROM openjdk:8-jdk-alpine

# Author/Maintainer information
LABEL authors="Tonimir"
LABEL maintainer="Tonimir"

# Use wanted Minecraft Forge version
ARG MINECRAFT_FORGE_VERSION
ARG FULL_MINECRAFT_FORGE_VERSION
ENV MINECRAFT_FORGE_VERSION ${MINECRAFT_FORGE_VERSION}
ENV FULL_MINECRAFT_FORGE_VERSION ${FULL_MINECRAFT_FORGE_VERSION}

# Update the package list
RUN apk update && apk upgrade

# Create the HudoNet Minecraft directory
RUN mkdir -p /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/

# Copy the Minecraft Forge installer to the container
COPY install/${MINECRAFT_FORGE_VERSION}/forge-${FULL_MINECRAFT_FORGE_VERSION}-installer.jar /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/

# Set working directory
WORKDIR /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/

# Install Minecraft Forge
RUN java -jar forge-${FULL_MINECRAFT_FORGE_VERSION}-installer.jar --installServer

# Rename Minecraft server jar
RUN mv minecraft_server.${MINECRAFT_FORGE_VERSION}.jar minecraft_server.jar

# Initial run to generate eula.txt
RUN java -jar minecraft_server.jar nogui

# Copy the eula.txt file to the container
COPY install/${MINECRAFT_FORGE_VERSION}/eula.txt /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/

# Copy all the configurations, OP list, player whitelist and banned IPs/players list to the container
COPY install/${MINECRAFT_FORGE_VERSION}/server.properties /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/
COPY install/${MINECRAFT_FORGE_VERSION}/ops.json /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/
COPY install/${MINECRAFT_FORGE_VERSION}/whitelist.json /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/
COPY install/${MINECRAFT_FORGE_VERSION}/banned-ips.json /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/
COPY install/${MINECRAFT_FORGE_VERSION}/banned-players.json /opt/hudonet/minecraft/${MINECRAFT_FORGE_VERSION}/
