# CrashPlanPRO Container with CrashPlanPRO Desktop App


To run this container, please use this command:


    docker run -d --name="CrashPlanPRO" \
           --net="bridge" \
           -p 4242:4242 \
           -p 4243:4243 \
           -p 4280:4280 \
           -v "/path/to/your/crashplanpro/config":"/config":rw \
           -v "/path/to/your/manifest/dir":"/backup":rw \
               computerheaven/crashplanpro

###Some supported variables:

####Variable TZ: 

This will set the correct timezone. Set yours to avoid time related issues.

```
-e TZ="America/Sao_Paulo"
```

####Variable HARDENED:

This will disable MPROTECT for grsec on Java executable (for hardened kernels).

```
-e HARDENED="Yes"
```

####Variable VNC_PASSWD:

This will enable password protection for your webui interface.

```
-e VNC_PASSWD="your_password"
```


###Ports:

This container ports can be changed, in bridge network mode, changing the "-p" switch from the run command, or, in host mode, using variables started by "TCP_PORT_" prefix.

####Port 4242 (TCP_PORT_4242): 

This port is used by CrashPlan for computer-to-computer backups.

```-p 4242:4242``` or ```-e TCP_PORT_4242=4242```


####Port 4243 (TCP_PORT_4243): 

This port is used by CrashPlan app to connect to CrashPlanPRO service.

```-p 4243:4243``` or ```-e TCP_PORT_4243=4243```

####Port 4280 (TCP_PORT_4280):

This port exposes a noVNC instance with the CrashPlanPRO Desktop App. 

```-p 4280:4280``` or ```-e TCP_PORT_4280=4280```

Then navigate to ```http://yourip:4280/vnc.html?autoconnect=true&host=192.168.0.100&port=4280``` to access the graphic user interface.

This container is only a simple modification of the Crashplan container which was built by gfjardim. However, this container is neither endorsed nor supported by gfjardim.