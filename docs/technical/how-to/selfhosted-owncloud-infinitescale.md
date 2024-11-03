---
tags: [aws, docker, owncloud, s3]
---

# Self-Hosted OwnCloud Infinite Scale with Docker

## Configuration

```  
IDM_CREATE_DEMO_USERS=false  
OCIS_DOMAIN=https://example.com  
PROXY_HTTP_ADDR=0.0.0.0:9200  
OCIS_URL=https://example.com

# Use AWS S3 Bucket for storage. So, you can keep minimal data on server  
STORAGE_USERS_DRIVER=s3ng  
STORAGE_SYSTEM_DRIVER=ocis  
STORAGE_USERS_S3NG_ENDPOINT=https://s3.eu-central-1.amazonaws.com  
STORAGE_USERS_S3NG_REGION=eu-central-1  
STORAGE_USERS_S3NG_ACCESS_KEY=*******  
STORAGE_USERS_S3NG_SECRET_KEY=*******  
STORAGE_USERS_S3NG_BUCKET=bucket-name  
```

## Start

### With Single Container

```shell  
docker run --rm -it -v ./ocis.yaml:/etc/ocis/ocis.yaml owncloud/ocis init  
docker run -p 9200:9200 -v ./ocis.yaml:/etc/ocis/ocis.yaml -v ocis-data:/var/lib/ocis -e IDM_CREATE_DEMO_USERS=true owncloud/ocis  
```

### With Docker Compose

Create ocis.yaml automatically

```  
docker run --rm -it -v ./:/etc/ocis owncloud/ocis init  
```

docker-compose.yml

```  
version: '3'

services:

  ocis:  
    image: owncloud/ocis  
    restart: always  
    env_file: .env  
    ports:  
      - "9200:9200"  
    volumes:  
      - ./config:/etc/ocis  
      - ./data:/var/lib/ocis  
```

Start

```  
docker compose up -d  
```  

> Unknown (2023-11-25 15:38:38)  
> #aws #docker #owncloud #s3

