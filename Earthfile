VERSION 0.8

IMPORT ./api AS api
IMPORT ./web AS web

FROM gcr.io/distroless/static-debian12

api-build:
    FROM api+build
    SAVE ARTIFACT build
    
web-build:
    FROM web+build
    SAVE ARTIFACT build

assemble:
    WORKDIR /app
    COPY +api-build/build/ ./
    COPY +web-build/build/ ./public/
    SAVE ARTIFACT ./ AS LOCAL cli

all:
    BUILD +assemble
