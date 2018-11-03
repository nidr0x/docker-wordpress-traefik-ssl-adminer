# WordPress on Docker with Traefik + SSL + Adminer
I developed this project with one pourpose: setup local WordPress development scenario with some interesting things.

## Getting started
The stack used is very common (and simple): 

* Traefik as a Load Balancer and SSL termination
* Watchtower to detect if any linked container have a new image version available, then automatically updating and restarting.
* MariaDB as database server.
* WordPress (captain obvious).
* Adminer as a database management, but i prefer to use other tools like MySQL Workbench for management.
* Bytemark/smtp container as a simple mail server to allow SMTP Host available as "mail".
* WP-CLI to be able to fill sample content and autoinstall WP without without doing any additional action.

### Prerequisites
You will need Docker and docker-compose installed on your machine. Depending of your operating system, the installation are very different. I personally recommend Arch Linux, because AUR is awesome.

### Install
Once you have checked the prerequisites, the first step is to clone the project with the next command:

```
git clone https://github.com/nidr0x/docker-wordpress-traefik-ssl-adminer.git
```

Next step, go inside the folder:

```
cd docker-wordpress-traefik-ssl-adminer 
```
If you want, you can customize some secrets and environment variables (like domains used) are stored in .env file. Also, Traefik configuration is available inside traefik/traefik.toml

Because the default PHP values are restrictive for a dev environment, you can put your own values inside php.ini file in the loaded Docker volume.

Finally, let the magic flow :-):
```
docker-compose up
```

And if you want to start without logs in silent mode:
```
docker-compose up -d
```
