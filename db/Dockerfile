FROM mysql:latest

ADD ./products.csv /products.csv
ADD ./users.csv /users.csv
ADD ./setup.sql /docker-entrypoint-initdb.d/setup.sql




ENTRYPOINT ["/entrypoint.sh"]
CMD ["mysqld", "--secure-file-priv=/"]
#CMD ["--secure-file-priv=/"]
