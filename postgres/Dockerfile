FROM centos:centos7
MAINTAINER Dean Efrati <deanefrati@gmail.com>

RUN yum install -y curl; yum upgrade -y; yum update -y;  yum clean all

RUN sed -i '19i exclude=postgresql*' /etc/yum.repos.d/CentOS-Base.repo \
	&& sed -i '28i exclude=postgresql*' /etc/yum.repos.d/CentOS-Base.repo

RUN cd ~ \
	&& curl -O http://yum.postgresql.org/9.4/redhat/rhel-7-x86_64/pgdg-centos94-9.4-1.noarch.rpm \
	&& rpm -ivh pgdg* \
	&& yum install -y postgresql94-server \
	&& rm -f pgdg-centos94-9.4-1.noarch.rpm \
	&& chown -R postgres:postgres /usr/pgsql-9.4/

ENV PG_HOME /usr/pgsql-9.4
ENV PATH $PG_HOME/bin:$PATH
WORKDIR $PG_HOME
USER postgres

RUN initdb -U postgres -D data/ \
	&& pg_ctl -D data/ -l pgsql.log start \
	&& sleep 5s \
	&& psql -c "CREATE ROLE app PASSWORD 'app' NOSUPERUSER CREATEDB NOCREATEROLE INHERIT LOGIN" \
        && createdb -U app -T template0 app \
	&& pg_ctl -D data/ stop -m fast \
	&& echo "host    all             all             0.0.0.0/0               trust" >> data/pg_hba.conf \
	&& sed -i "59i listen_addresses = '*'" data/postgresql.conf \
	&& echo "postgres -D data/" > startup.sh \
	&& chmod +x startup.sh

EXPOSE 5432

USER postgres

CMD bash -C 'startup.sh'
