FROM pymor/jupyter_py3.8:6482589aa9345c76ae77437661ecb4d67a1963d4
MAINTAINER rene.fritze@wwu.de

# binder wants to set the NB_ vars
ARG NB_USER
ARG NB_UID

USER root
RUN useradd -d /pymor --shell /bin/bash -u ${NB_UID} -o -c "" -m ${NB_USER}

# do local package install before requirements to avoid conflict
COPY requirements.txt /tmp/
RUN pip install -Ur /tmp/requirements.txt && rm /tmp/requirements.txt
USER ${NB_USER}

COPY tutorials /pymor/tutorials
 COPY exercises /pymor/exercises

ENV JUPYTER_TOKEN=${PYMOR_JUPYTER_TOKEN} \
    USER=${NB_USER} \
    HOME=/pymor

ENTRYPOINT []
WORKDIR /pymor/
