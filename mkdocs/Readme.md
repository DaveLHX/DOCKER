This image is used to generate the static mkdocs html site.

```shell
docker build -t mkdocs:latest .
```

Then you can run a container (--rm will remove the container after the mkdocs build command completes)
\${PWD} should be the folder where you mkdocs.yml file is located

To build the doc

```shell
docker run --rm -ti --name mkdocsBuild  -v ${PWD}:/workdir  mkdocs:latest mkdocs build
```

to serve the doc

```shell
docker run --rm -ti --name mkdocsServe -p 86:8000  -v ${PWD}:/workdir  mkdocs:latest mkdocs serve
```
