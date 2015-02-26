#Links

##How to find if a container is linked to another container


###Option 1
    docker inspect elk_kibana4 | fgrep -A1 Links

looks through the inspected output of the container.  Locates the "Links" config and shows the following line which contains the information you're looking for. 


###Option 2
    docker inspect -f "{{ .HostConfig.Links }}" elk_kibana4

the -f flag means to format out the output.

##How to quit out of a container without shutting it down 

    Press the key combo ctrl + p + q

##How to use the alias for allowing communcation between containers

    docker run -d --name="elk_kibana4_server" -p 5601:5601 --link=elk_elasticsearch_server:elasticsearch privrepo:elk_kibana4_server_v1 ; docker logs -f elk_kibana4_server

If you notice the --link flag the pattern --link=[container]:[alias]

note this second portion, the alias portion can be used to reference the container within the container trying to reach out.  In the ELK example.
The kibana container must talk with the Elasticsearch container to work.  This alias "elasticsearch" is referenced in the kibana.yml.
