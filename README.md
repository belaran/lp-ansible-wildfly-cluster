README
====

Ce projet démontre la mise en place d'un cluster Wildfly de 3 instances, toutes hébergées par le même système. Il a été testé au sein d'un conteneur Docker basé sur Fedora:


    $ #!/bin/bash
    readonly DOCKER_IMAGE=${1:-'fedora'}
    readonly WORKSPACE="${WORKSPACE:-$(pwd)}"
    
    readonly CID=$(sudo docker run -ti --rm -v /sys/fs/cgroup:/sys/fs/cgroup:ro -v "${WORKSPACE}:/work/:rw" --privileged -d "${DOCKER_IMAGE}" '/usr/sbin/init')
    sudo docker exec -ti "${CID}" '/bin/bash'
    
