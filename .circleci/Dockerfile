FROM phusion/passenger-ruby21:0.9.10

EXPOSE 3000

RUN rm -f /etc/service/nginx/down

RUN apt-get update
RUN apt-get -y install sqlite3 libsqlite3-dev

ADD nginx/rails-env.conf /etc/nginx/main.d/rails-env.conf
ADD nginx/webapp.conf /etc/nginx/sites-enabled/webapp.conf
ADD . /home/app/webapp

WORKDIR /home/app/webapp
RUN bundle install

WORKDIR /home/app/webapp
RUN RAILS_ENV=production rake db:migrate

CMD ["/sbin/my_init"]

