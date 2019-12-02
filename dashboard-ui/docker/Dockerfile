FROM nginx

USER root

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git curl gnupg

RUN curl -sL https://deb.nodesource.com/setup_12.x  | bash -
RUN apt-get -y install nodejs

RUN git clone https://github.com/timursayfullin/dashboard-ui /tmp/dashboard-ui && \
    cd /tmp/dashboard-ui && \
    npm install && \
    npm run-script build

RUN rm -rf /usr/share/nginx/html/* && \
    mv /tmp/dashboard-ui/build/* /usr/share/nginx/html/
