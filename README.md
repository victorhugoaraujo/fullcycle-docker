## :scroll: Project description

This project was created to apply multistage building using Nginx as a reverse proxy

## :hammer: Technologies
The following technologies was used to made this project:

-  [Docker](https://www.docker.com/)
-  [Laravel Nginx config](https://laravel.com/docs/9.x/deployment#nginx)

## :iphone: Running the application
```bash
To run the application please follow the next steps:

# Clone this repository
git clone https://github.com/victorhugoaraujo/docker.git

# Go into the repository
$ cd docker

# Create a network
$ docker network create <name>

# Build laravel container
$ docker build -t victorhugoaraujo/laravel:prod laravel -f laravel/Dockerfile.prod

# Go into nginx directory
$ cd nginx

# Build nginx container
$ docker build -t victorhugoaraujo/nginx:prod . -f Dockerfile.prod

# Run laravel container
$ docker run -d --network <network-name> --name laravel victorhugoaraujo/laravel:prod

# Run nginx container
$ docker run -d --network <network-name> --name nginx -p 8080:80 victorhugoaraujo/nginx:prod

# Go to your browser
localhost:8080
```

Made with ♥ by Victor Hugo :wave: [Get in touch!](https://www.linkedin.com/in/victor-hugo-araujo-a73964115/)