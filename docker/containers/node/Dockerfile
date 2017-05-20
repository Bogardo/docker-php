FROM node:7.10

MAINTAINER Chris Bogaards

RUN npm install gulp-cli -g \
    && npm install webpack -g \
    && npm install grunt-cli -g

WORKDIR /var/www/html

CMD ["tail", "-f", "/dev/null"]