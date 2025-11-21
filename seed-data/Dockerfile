FROM alpine:3.19

WORKDIR /app

# install apache benchmark + curl
RUN apk add --no-cache apache2-utils curl

# copy script + post data files
COPY generate-votes.sh .
COPY posta .
COPY postb .

# make script executable
RUN chmod +x generate-votes.sh

CMD ["./generate-votes.sh"]

