# rome
A new build system for SugarCRM [![Build Status](https://travis-ci.org/jwhitcraft/rome.svg?branch=master)](https://travis-ci.org/jwhitcraft/rome)

## Updating (Currently does not work)
To update rome, just run `rome self-update`

## Usage

### Build
This command will build all the files inside the source directory

`rome build --version=7.9.0.0 --flavor=ent --destination=/tmp/sugar-build /path/to/mango/checkout/sugarcrm`


[more info](docs/rome_build.md)

### Watch
This command will keep a process running and build each file as it's created or modified (experimental!)

`rome watch --version=7.9.0.0 --flavor=ent --destination=/tmp/sugar-build /path/to/mango/checkout/sugarcrm`

[more info](docs/rome_watch.md)

## Help

[View the full help here](docs/rome.md)

## Building Rome
Make sure that you have golang installed

### Install dependencies for compiling
`go mod vendor`

### Compile
`make clean; make -e VERSION=2.0.0AlphaX`

## docker
Build the docker image:
```
docker build -t registry.sugarcrm.net/rome:latest .
```

Generate a build using the docker image and volume mounts:
```
docker run -it --rm -v /path/to/mango/sugarcrm:/sugarcrm -v /tmp/sugarcrm-build:/sugarcrm-build --name rome registry.sugarcrm.net/rome:latest go-wrapper run build /sugarcrm -d /sugarcrm-build -f ent -v 7.8.0.0
```
