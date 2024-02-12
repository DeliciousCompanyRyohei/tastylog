FROM node:20-alpine

# Python と build-tools のインストール
RUN apk add --no-cache python3 py3-pip make g++

COPY . /home/node/webapp

# 作業ディレクトリを設定
WORKDIR /home/node/webapp

# docker-entrypoint.sh を /usr/local/bin に移動し、実行可能に設定
RUN mv docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh && \
    chmod +x /usr/local/bin/docker-entrypoint.sh

# npm パッケージをインストール
RUN npm install

ENV MYSQL_HOST="127.0.0.1"
ENV MYSQL_PORT="3306"
ENV MYSQL_USERNAME="YOUR-MYSQL-USERNAME"
ENV MYSQL_PASSWORD="YOUR-MYSQL-PASSWORD"
ENV MYSQL_DATABASE="tastylog"

EXPOSE 3000

WORKDIR /home/node/webapp
ENTRYPOINT [ "docker-entrypoint.sh" ]
CMD [ "npm", "start" ]