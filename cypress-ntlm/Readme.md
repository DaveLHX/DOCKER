This image uses the official cypress image with the addition of cypress-ntlm-auth and an override of the entrypoint.   

The docker image cant communicate to your network with DNS names.  You must either use host.docker.internal to comunicate with the host or use ip addresses.  For example in our cypress.json we have somethign like this
"baseUrl": "http://localhost:8080/#/" => this wont work.
"baseUrl": "http://host.docker.internal:8080/#/" => this works.
"baseUrl": "http://ip.of.host:8080/#/" => this works.


To build the image
```shell
docker build -t cypress-ntlm:3.6 .
```

To run the image and create the new container bound to the current directory  (should be the root folder of your project).  This will automatically start a headless test run with electron and remove the image after the run is complete
```shell
docker run --rm -it --name cypress-ntlm -v ${PWD}:/e2e -w /e2e cypress-ntlm:3.6
```


