This image uses the official cypress image with the addition of cypress-ntlm-auth and an override of the entrypoint.   

To build the image
```shell
docker build -t cypress-ntlm:3.6 .
```

To run the image and create the new container bound to the current directory  (should be the root folder of your project).  This will automatically start a headless test run with electron and remove the image after the run is complete
```shell
docker run --rm -it -v --name cypress-ntlm ${PWD}:/e2e -w /e2e cypress-ntlm:3.6
```


