

# user.yml
- Create a user named hng with sudo privileges.
a

# database.yml
- install postgress server, client, utils with apt
- initialize db
- start and enable postgress service
- run my postgress query --------------------------------->>>>>
- sql query flush        --------------------------------->>>>>
- Create a postgress database for app
- Create a postgress user for app with password
- Save the admin user and credentials in /var/secrets/pg_pw.txt
- Enable remote login to postgress


# app.yml
- Clone your repository into the /opt directory with the name stage_5b (i.e., /opt/stage_5b), and ensure it is owned by the hng user.
- Checkout to Devops Branch
- Change file ownership, group and permissions
- copy .env file to the app directory

- Install app dependencies with `go mod download`
- build app with `go build -o production_app main.go`
- Ensure your application starts on port 3000.

# Configure Service for go
- Create a systemd service file for the app
- Enable the app
- Start it

# proxy.yml
- Set up Nginx to reverse proxy your application to port 80 via the conf file
- Configure stderr logs to be saved in /var/log/stage_5b/error.log and stdout logs in /var/log/stage_5b/out.log.
- Ensure both log files are owned by the hng user.
- move conf file from templates to /etc/nginx/sites-available
- link file in sites-available to sites-enabled
- restart nginx


# Dependencies
- ubuntu 22.04 ------------ ansible-server
- python 3.12  ------------ ansible-server
- postgres --------- deployment-server
- golang 1.19 --------- deployment-server
- nginx 1.26 --------- deployment-server
- pm2
