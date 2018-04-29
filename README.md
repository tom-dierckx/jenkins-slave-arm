# ARM V7 32bit compatible jenkins slaves
I did not created this content I found the Docker files on:  https://hub.docker.com/r/jenkins/jnlp-slave/ and https://hub.docker.com/r/jenkins/slave/.

I just modified the Docker images to work on ARM devices like the raspberry pi.

I have build and uploaded these images to hub.docker.io on:

* [Base slave image](https://hub.docker.com/r/tomdierckx/jenkins-arm-slave/)
* [JNPL slave image](https://hub.docker.com/r/tomdierckx/jenkins-arm-slave-jnlp/)

Using this image in the scripted pipeline (as if one was using a kubernetes cluster on raspberry pi's) on would have to add the following:

```
podTemplate(label: label, containers: [
    containerTemplate(name: 'jnlp', image: 'tomdierckx/jenkins-arm-slave-jnlp:0.0.2', args: '${computer.jnlpmac} ${computer.name}')
    ]) {
```

Tested this on Raspberry pi 3b using Jenkins version 2.118 with kubernetes plugin version 1.6.0 .