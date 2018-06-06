FROM cn007b/go:1.10

MAINTAINER Vladimir Kovpak <cn007b@gmail.com>

# gcloud
RUN export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" && \
    echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - && \
    apt-get update -y && apt-get install google-cloud-sdk -y

# goapp 1.9
RUN apt-get install -y google-cloud-sdk-app-engine-go \
  && ln -s /usr/lib/google-cloud-sdk/platform/google_appengine/goroot-1.9/bin/goapp /usr/local/bin
