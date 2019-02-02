redhawk-yum
===============
This project creates a local yum repository server hosting REDHAWK release artifacts.


Quickstart
----------
```bash
# (May be required) Local yum server is hosted on port 8080 by default - Ensure firewall allows http on 8080
sudo firewall-cmd --add-port=8080/tcp

# Start yum server with REDHAWK artifacts
docker-compose up --build -d
```

### Yum Container
The yum container unpacks a REDHAWK tarball and hosts the artifacts on an httpd server.
The yum server is hosted on port 8080 (by default) and can be viewed in a browser at 
[http://localhost:8080/yum](http://localhost:8080/yum).


#### Updating REDHAWK Version and Yum Port
The [.env](.env) file defines the location of the REDHAWK tar (REDHAWK_TAR) and the yum-servers port (YUM_PORT).
Additional REDHAWK tarball releases can be found on github at <https://github.com/RedhawkSDR/redhawk/releases>.


#### Slow/No Internet Connection?
A local REDHAWK tarball may be loaded into the container by **copying the tarball inside this git repository.**
To override the REDHAWK_TAR variable, define the relative tarball path in the [.env](.env) file.
```bash
REDHAWK_TAR=./redhawk-yum-2.2.1-el7-x86_64.tar.gz
```
