# docker build -t ubuntu1604py36
FROM ubuntu:18.04

RUN apt-get update && apt-get install -y software-properties-common 
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update -y

RUN apt-get install -y build-essential python3.8 python3.8-dev python3-pip python3.8-venv && apt-get install -y git

# update pip
RUN python3 -m pip install wheel
RUN git clone https://github.com/hat/pyShelf.git /usr/src/app/
RUN python3 -m pip install -r /usr/src/app/requirements.txt
EXPOSE 8000

WORKDIR /usr/src/app/src/
#RUN ../docker/scripts/wait-for-it.sh db:5432
RUN python3 manage.py migrate
#RUN python3 manage.py migrate interface
CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]
