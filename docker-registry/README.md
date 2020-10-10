# Docker Registry

## Run
Run image as daemon:
`docker run -d --name registry -p 5000:5000 --restart=always registry:2`

Run image interactively:
`docker run -it --rm --name registry -p 5000:5000 --restart=always --name registry registry:2`

## Useful links
* https://docs.docker.com/registry/deploying/