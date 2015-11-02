# Tips for Docker

it is not possible to set an ENV variable inside a container.

Workaround:
1/ Create your own script, which will act like runner for your command. For example:
    #!/bin/bash
    export VAR1=VAL1
    export VAR2=VAL2
    your_cmd

2/ Run your command following way:
    docker exec -i CONTAINER_ID /bin/bash -c "export VAR1=VAL1 && export VAR2=VAL2 && your_cmd"

3/ stop docker daemon and change container config in:
    /var/lib/docker/containers/[container-id]/config.json



find container-id:
    docker inspect [container-name]

list images
    sudo docker images --all

commit modification on build container
    sudo docker commit 4a24c4bb99db multinest


