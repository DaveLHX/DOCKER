This image can be used to run the QUASAR-CLI and unit tests and build a quasar app.  It intalls the latest Quasar CLI at the time of the build.  There is no cypress in this image, it does not work with alpine. for it we use the official cypress image as a base but its much bigger than this one. 

To build the image run this command in the same folder as the docker file
```shell
docker build -t quasar:cli-latest .
```

To run the image and create the new container bound to the current directory (root folder of your project).  
This container will start ready for commands.
```shell
docker run -ti -d --name quasar-cli  -v ${PWD}:/workdir -p 85:4000  quasar:cli-latest 
```

Example commands.
```shell
docker exec -i quasar-cli npm run test:unit:coverage
docker exec -i quasar-cli quasar build
#-d detached, we dont want to wait for this to stopn otherwise it would hang the pipeline.
docker exec -d quasar-cli quasar serve dist/spa/  -p 4000
```

Remove the container at the end of the pipeline
```shell
docker rm quasar-cli 
```


npm install in the container does not cache the .npm files for the next 'run' command


docker run -ti -d --name quasarCypress  -v ${PWD}:/workdir -p 85:4000  quasar:cypress