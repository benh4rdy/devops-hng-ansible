# Automated Deployment and Configuration with Ansible for Boilerplates

## Overview

This project involves configuring an instance of a Golang application boilerplate using Infrastructure as Code (IaC) with Ansible. The goal is to automate the deployment and setup of the boilerplate application on a remote Linux server (Ubuntu 22.04).

## Ansible Playbook: main.yaml

### Tasks

1. **Clone:**
   - Clone the `devops` branch of the [boilerplate repository](https://github.com/hngprojects/hng_boilerplate_golang_web/tree/devops) to a remote Linux server (Ubuntu 22.04).

2. **Install Dependencies and Deploy:**
   - Install all dependencies required for the boilerplate to run, including databases.
   - Build and deploy the boilerplate application on the server.

3. **Setup PostgreSQL:**
   - Configure a PostgreSQL database.
   - Save the admin user and credentials in `/var/secrets/pg_pw.txt`.

4. **Application Configuration:**
   - Ensure the application starts on port 3000.
   - Set up Nginx to reverse proxy the application to port 80.

5. **Logging:**
   - Configure stderr logs to be saved in `/var/log/stage_5b/error.log` and stdout logs in `/var/log/stage_5b/out.log`.
   - Ensure both log files are owned by the `hng` user.

## Walkthrough of the Ansible Playbook

### User and Directory Setup

1. **Create a User:**
   - On the Linux server, a user named `hng` is created with sudo privileges.

2. **Clone Repository:**
   - Clones the `devops` branch of the [boilerplate repository](https://github.com/hngprojects/hng_boilerplate_golang_web/tree/devops) into the `/opt` directory of the remote server with the name `stage_5b` (i.e., `/opt/stage_5b`), and ensure it is owned by the `hng` user.

### Database and Dependencies

1. **Install PostgreSQL:**
   - Installs PostgreSQL and save the admin credentials in `/var/secrets/pg_pw.txt`.

2. **Install Dependencies:**
   - Installs all application and database dependencies.
   - Configures the environment variables, application properties, or application settings accordingly.

### Application and Proxy Setup

1. **Run Application:**
   - Ensures the application is running on `127.0.0.1:3000` without exposing port 3000 externally.

2. **Install Nginx:**
   - Installs Nginx 1.26 and configure it to reverse proxy requests from port 80 to the application.

### Logging Configuration

1. **Set Up Logging:**
   - Sets up logging so that stderr logs are written to `/var/log/stage_5b/error.log` and stdout logs to `/var/log/stage_5b/out.log`.
   - Ensures both log files are owned by the `hng` user.

## Summary

This project automates the deployment and configuration of a boilerplate application using Ansible. By following the instructions and tasks outlined above, the application should be successfully deployed, with dependencies installed, PostgreSQL configured, Nginx set up as a reverse proxy, and proper logging established. The `hng` user will have the necessary permissions to manage the setup, ensuring a streamlined and secure deployment process.
