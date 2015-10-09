

###*Updated to work with SDK3.6dp6*

#QUICKSTART COMMAND

```
docker run -v <root/dir/of/my/project>:/pebble  -e PEBBLE_PHONE=<IP ADDRESS> docker-pebble-dev <pebble command arguments>
```


*Special Thanks to Andres Dumas | Forked from andredumas/pebble-dev |  His notes below: *

# Supported tags and respective `Dockerfile` links

* [`2.8.1` (*2.8.1/Dockerfile*)](https://github.com/andredumas/docker-pebble-dev/blob/2.8.1/Dockerfile)
* [`3.0` (*3.0/Dockerfile*)](https://github.com/andredumas/docker-pebble-dev/blob/3.0/Dockerfile)
* [`3.2` (*3.2/Dockerfile*)](https://github.com/andredumas/docker-pebble-dev/blob/3.2/Dockerfile)

# What is Pebble?

> [Pebble Smartwatch](https://getpebble.com/) is a customizable watch that conveniently and subtly delivers the information that you want directly to your wrist. Pebble connects to your iOS or Android smartphone via Bluetooth and has a rechargeable battery that lasts up to 7 days per charge.

* https://getpebble.com
* https://en.wikipedia.org/wiki/Pebble_watch
 
# What's in this image?

The pebble [development SDK](http://developer.getpebble.com/sdk/install/linux/) installed and ready for usage. 

http://developer.getpebble.com/sdk/

# How to use this image

```
docker pull cesleem/pebble-dev
```

Standard usage, assuming you are running from the root of your project, is to use it to execute pebble commands:

```
docker run --rm -it -v $PWD:/pebble pebble-dev <pebble command arguments>
```

Or drop the `pebble` shell script in the root of your project or PATH.

For Pebble SDK 2.8.1 development I was using the below `Makefile` configured with [Eclipse](https://eclipse.org/downloads/) 
Luna [C/C++](http://www.eclipse.org/downloads/packages/eclipse-ide-cc-developers/marsr). 

```
all:
	./pebble build

install:        all
	./pebble install --pebble_id `cat $(HOME)/.pebble-btid`
	./pebble logs

clean:
	./pebble clean
```

The following run profiles were also used:

```
./pebble install --phone 192.168.1.20
```

And:

```
./pebble logs --phone 192.168.1.20
```

## Notes

When running as pebble executable with a mounted volume, any files created by the container will be on the host owned 
as `root`.