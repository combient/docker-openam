# docker-openam

based on wdijkerman/openam:13.0.0

This container is running a Java 8 with Tomcat 8 for OpenAM. 

# Usage

Using the container can be done like this:

```
docker pull combient/openam:latest
docker run -d -h openam.example.com --name openam -p 8080:8080 combient/openam:latest
```

This will bootup the container and start OpenAM. You'll have to make sure you put `127.0.0.1  openam.example.com` in your hosts file, otherwise you can't access OpenAM.
Check the logs to see when the container is booted correctly:
```
docker logs -f openam
```
Output will be like:
```
Registering service amAuthSAML2.xml...Success.
Registering service audit.xml...Success.
Registering service RadiusServerService.xml...Success.
Registering service amSessionPropertyWhitelist.xml...Success.
Registering service selfService.xml...Success.
Configuring system....Done
Configuring server instance....Done
Creating demo user....Done
Setting up monitoring authentication file.
Configuration complete!
```

Configuration is complete and you should be able to open the login page by opening the following url:
```
http://openam.example.com:8080/openam/XUI/#login/
```

# Version

You can verify which OpenAM is running by opening the following url:
```
$ curl 'http://openam.example.com:8080/version'
13
```

# Credentials

The following credentials can be used:

## OpenDJ

```
Username: cn=Directory Manager
Password: password_opendj
```

## OpenAM

```
Username: amadmin
Password: password_openam
```

**note:**
This container is not suitable for production environments, there are no volumes for storing data and an "embedded" OpenDJ is used.
