FROM mariadb:latest

ENV MARIADB_ROOT_PASSWORD=123

COPY student-rds.sql /docker-entrypoint-initdb.d/

EXPOSE 3306

CMD ["mariadb"]