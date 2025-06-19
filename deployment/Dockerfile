FROM jupyter/base-notebook:python-3.10

USER root
RUN usermod -l kyoon jovyan \
 && usermod -d /home/kyoon -m kyoon \
 && groupmod -n kyoon users

RUN apt-get update \
 && apt-get install -y gcc python3-dev fontconfig fonts-nanum libssl-dev cron vim tzdata \
 && fc-cache -fv

ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && echo Asia/Seoul > /etc/timezone

ENV NB_USER=kyoon
ENV HOME=/home/kyoon
WORKDIR /home/kyoon

COPY requirements_local.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

COPY requirements_notebook.txt /requirements_notebook.txt
RUN pip install --no-cache-dir -r /requirements_notebook.txt

USER ${NB_USER}
