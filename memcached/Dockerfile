FROM phusion/baseimage:0.9.19
MAINTAINER anhducbkhn
RUN apt-get update
RUN apt-get install -y memcached
EXPOSE 11211
CMD [ "-m", "128"]
USER daemon
ENTRYPOINT memcached

