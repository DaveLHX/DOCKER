##Creating a Container
To optimize loading time we want to preload as much stuff as possible in our image.  For example if we make an image with with MkDocs it can be worth it to pre build our image so that when we run the image the items are already installed.

To make an mkdocs image
```dockerfile
FROM jfloff/alpine-python:latest
RUN \ 
    pip install mkdocs && \
    rm -rf /tmp/* /var/tmp/* /var/cache/apk/* /var/cache/distfiles/*
WORKDIR /workdir
```
Then from the folder containing the dockerfile we could build the image
```shell
docker build -t mkdocs:newImage .
```

Then you can run a container  (--rm will remove the container after the mkdocs build command completes) 
```shell
docker run --rm -ti --name mkdocsBranch1  -v G:/Code/mkdocsTest/Docker/mkdocs:/workdir  mkdocs:newImage mkdocs build
```


image that can. (set the workdir match to a volume)
npm install
quasar build (stay open)

//different step and we want the result.
exec npm run test:unit:coverage

//different step paralel to previous one
run a docker that hosts the website
run a docker that runs cypress tests


dockerfile -> image -> container