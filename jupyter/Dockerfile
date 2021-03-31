
FROM jupyterhub/jupyterhub

MAINTAINER neo "neo@neo1989.net"


RUN apt-get update

WORKDIR /srv/jupyterhub

RUN mkdir ~/.pip/
COPY ./pip.conf ~/.pip/

RUN curl -fsSL https://deb.nodesource.com/setup_12.x |  bash -

RUN apt install gcc g++ make nodejs vim -y

RUN pip install jupyter jupyterlab jupyterhub matplotlib XlsxWriter pandas xlrd

RUN jupyter labextension install jupyterlab-spreadsheet

RUN useradd -ms /bin/bash admin
RUN echo "admin:admin" | chpasswd

RUN jupyterhub --generate-config

COPY ./jupyterhub_config.py /srv/jupyterhub/jupyterhub_config.py

EXPOSE 8000
CMD ["jupyterhub"]
