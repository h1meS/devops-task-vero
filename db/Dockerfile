FROM mcr.microsoft.com/mssql/server:2022-latest

USER root

ENV ACCEPT_EULA Y
ENV MSSQL_SA_PASSWORD Un!q@to2023

COPY db.sql ./db.sql

CMD ["/opt/mssql/bin/sqlservr"]
