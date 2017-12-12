demonstration of chrome 63's breaking of the `--unsafety-treat-insecure-origin-as-secure` flag 

`docker-compose up` will spin up a simple nginx server and a selenium server (with chrome)

Once launched nginx will serve a simple webpage on 8080 consisting of an import of a dummy serviceworker (serviceworkers require secure origins)

The docker image includes chrome 63 via selenium. you can access the docker image there via vnc on 6080. Once vnced in you can launch a chrome with the appropriate options.
  - right click desktop
  - applications -> shells -> bash
  - `google-chrome --unsafely-treat-insecure-origin-as-secure=http://172.17.0.1:8080 --user-data-dir=/tmp/foo/`
  
Navigate to 172.17.0.1:8080 (docker's magic ip for the host and the 8080 port the docker compose exposes). This will call up the index page. `inspect -> console` to see that an error specifying only secure origins are allowed even with the flag
