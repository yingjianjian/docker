FROM redis:4.0.11
RUN apt-get update -y
RUN apt-get install -y  ruby \
rubygems
RUN apt-get clean all
RUN gem install redis
RUN apt-get install dnsutils -y
RUN sed -i "s/:password => nil,/:password => 'QjdChina41',/g" /var/lib/gems/2.3.0/gems/redis-4.1.0/lib/redis/client.rb
ADD redis-trib.rb .
~

