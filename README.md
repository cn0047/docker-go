## GO for DEVELOPMENT.

[![Docker Build Status](https://img.shields.io/docker/build/cn007b/go.svg)](https://hub.docker.com/r/cn007b/go/)
[![Docker Automated build](https://img.shields.io/docker/automated/cn007b/go.svg)](https://hub.docker.com/r/cn007b/go/)
[![Docker Pulls](https://img.shields.io/docker/pulls/cn007b/go.svg)](https://hub.docker.com/r/cn007b/go/)

This image contains pre-installed tools helpful for development purposes.
<br>Also this image can be used as part of build process (lint, test, cover, etc.)

# List of installed tools:

* golint
* gometalinter
* cover
* goveralls
* dlv
* gin
* pprof
* google-app-enginee

# Usage:

### CLI:

Create test package with purpose to check this docker image:

````go
package main

func main() {
    println("It works!")
}
````

Now you can run next command:

````sh
docker run -it --rm -v $PWD:/app -w /app cn007b/go go run main.go
````

### Web

````go
package main

import (
	"net/http"
)

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		w.Write([]byte("Hello world!"))
	})
	http.ListenAndServe(":8080", nil)
}
````

Now you can run next command:

````sh
docker run -it --rm -p 80:80 -v $PWD:/app -w /app cn007b/go sh -c \
  'gin --port 80 --appPort 8080 run main.go'

# and
curl localhost:80
````

# Google App Enginee:

With purpose to use `google-app-enginee` please use next commands:

````sh
docker run -it --rm cn007b/go:1.10-gae gcloud version
docker run -it --rm cn007b/go:1.10-gae goapp version
````
