FROM mcr.microsoft.com/mssql/server:2022-latest

USER root

# Create a config directory
RUN mkdir -p /usr/config
WORKDIR /usr/config

# Bundle config source
COPY . /usr/config
RUN chmod +x /usr/config/entrypoint.sh
RUN chmod +x /usr/config/configure-db.sh

ENTRYPOINT ["./entrypoint.sh"]

# Tail the setup logs to trap the process
CMD ["tail -f /dev/null"]

# Just an MVP, y'all.
HEALTHCHECK CMD [ "sqlcmd", "-Q", "select 1" ]