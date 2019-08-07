FROM nginx:1.16.0-alpine

ADD nginx.conf /etc/nginx/
ADD service-contest.conf /etc/nginx/sites-available/

#RUN ln -s /etc/nginx/sites-available/x.conf /etc/nginx/sites-enabled/x

RUN ls -la /etc/nginx/
RUN ls -la /etc/nginx/sites-available

#RUN usermod -u 1000 www-data
RUN addgroup -S app-group && adduser -S www-data -G app-group

CMD ["nginx"]

EXPOSE 80
EXPOSE 443