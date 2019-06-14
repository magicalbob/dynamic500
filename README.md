Using a backup nginx server to serve 5xx error pages when proxy is down

Build local:nginx docker image first:

	docker build -t local:nginx nginx

Then run `docker-compose up` to bring up the cluster.

Now `curl 127.0.0.1:8000` and you should get "THIS IS SERVER 2".

Do a `docker exec -ti nginx_nginx2_1 bash` to get on the many end point and do `systemctl stop nginx`.

Do `curl 127.0.0.1:8000` again and you should get "THIS IS SERVER 3".

If you then docker exec on to nginx3 and stop nginx on it, nginx1 will serve it's static 500 series error page.

`nginx2` and `nginx3` do not have to be nginx servers. They could be micro services (e.g. node or java apps). `nginx2` being the micro service that does the day-to-day business, and `nginx3` being a micro service that serves up 500 series pages (e.g. a service that checks if a planned maintenance is currently scheduled and presents a nice informative page for it).
