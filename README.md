redhawk-yum
===============
This project creates a local yum repository server hosting REDHAWK release artifacts.


Quickstart
----------
```bash
# Local yum server is hosted on port 8080 by default - Ensure firewall allows http on 8080
sudo firewall-cmd --add-port=8080/tcp

# Start yum server with REDHAWK artifacts
docker-compose up --build -d
```

### Yum container
The yum container will download a REDHAWK tarball, unpack the RPMs and start an httpd server.
The yum server is hosted on port 8080 (by default) and can be viewed in a browser at 
[http://localhost:8080/yum](http://localhost:8080/yum).


#### Updating REDHAWK version and YUM_PORT
The [.env](.env) file contains configuration for modifying which REDHAWK tarball to use and which port
yum should use on the host.
Additional REDHAWK tarball releases can be found on github at <https://github.com/RedhawkSDR/redhawk/releases>.


#### Slow/No internet connection?
A local REDHAWK tarball may be loaded into the container by **copying the tarball inside this git repository.**
To override the REDHAWK_TAR variable, define the relative tarball path in the [.env](.env) file.
```bash
REDHAWK_TAR=./redhawk-yum-2.2.1-el7-x86_64.tar.gz
```
