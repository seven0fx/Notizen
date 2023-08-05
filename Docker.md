list running images:

      docker container ls -a

shell öffnen:

      docker exec -it $(docker ps -f name=addon_core_nginx_proxy -q) bash
