phoebus-env
===
Configuration Environment for  ControlSystemStudio Phoebus at https://github.com/ControlSystemStudio/phoebus

## Role
In order to download, install, setup all relevant components, one should do many steps manually. This repository was designed for the easy-to-reproducible environment for ControlSystemStudio/phoebus

## Requirements


### Apache Tomcat Native Library and Maven

* Debian 10

```
apt install maven openjfx libopenjfx-java
```


* CentOS 7

```
yum install maven
```


* CentOS 8 & Fedora 31
One can use `yum` instead of `dnf`. `epel-release` is needed. 
```
dnf install maven
```




### JDK 8 or newer
* Debian 10
```
openjdk version "11.0.6" 2020-01-14
OpenJDK Runtime Environment (build 11.0.6+10-post-Debian-1deb10u1)
OpenJDK 64-Bit Server VM (build 11.0.6+10-post-Debian-1deb10u1, mixed mode, sharing)
```

* Fedora 31
```
openjdk version "1.8.0_242"
OpenJDK Runtime Environment (build 1.8.0_242-b08)
OpenJDK 654-Bit Server VM (build 25.242-b08, mixed mode)
```


## Few Makefile Rules

### `make init`
* Download phoebus
* Switch to a specific version defined in `$(SRC_TAG)` in `configure/RELEASE`

### `make build`
* Build the phoebus, located in `phoebus-src/phoebus-product/target`.

### `make conf`

### `make install`
* `sudo` permission may be required.
* Rename `product-*.jar` to `pheobus-*.jar`, and install it in `target` path into `INSTALL_LOCATION` defined in `configure/CONFIG_SITE`
* Install `lib` path in `target` path into `INSTALL_LOCATION` defined in `configure/CONFIG_SITE`
* Install phoebus luncher into `bin` in `target` path
* Install `settings.ini` into `INSTALL_LOCATION`. 

### `make distclean`
* Remove the downloaded phoebus source file

### `make vars`
* Print out interesting variables
* One can use `make PRINT.VARIABLE_NAME` to print out them. For example,  `make PRINT.INSTALL_LOCATION`.

## A typical example to configure the Phoebus 


```
$ make init
$ make conf
$ make build
```

## Customize site-specific configuration
Please consult two files in `configure` path, such as `RELEASE` and `CONFIG_SITE`. There are few comments on there. If you are familiar with the standard EPICS building system [1], it should be easy to understand them, because we mimic that concept into this repository. 


## Reference

[1] https://epics-controls.org/


