# gollum
a personal wiki.  
needs git

[explanations](https://github.com/gollum/gollum/wiki/Gollum-via-Docker)

## create git folder
```
mkdir DIR
cd DIR
git init
```

## Dockerfile


create a file **Dockerfile**
```
FROM ruby:2.7
RUN apt-get -y update && apt-get -y install libicu-dev cmake git && rm -rf /var/lib/apt/lists/*
RUN gem install github-linguist
RUN gem install gollum
RUN gem install org-ruby  # optional
WORKDIR /wiki
ENTRYPOINT ["gollum", "--port", "80"]
EXPOSE 80
```

## build the docker image
`docker build -t gollum .`

## run the image
```
cd DIR
docker run -d --name=gollum -v $(pwd):/wiki -p 4567:80 gollum
```

## accessin the gollum GUI
`http://127.0.0.1:4567`


