#Links

##How to find if a container is linked to another container


###Option 1
    docker inspect elk_kibana4 | fgrep -A1 Links

looks through the inspected output of the container.  Locates the "Links" config and shows the following line which contains the information you're looking for. 


###Option 2
    docker inspect -f "{{ .HostConfig.Links }}" elk_kibana4

the -f flag means to format out the output. 
