#DockerFile


# multiple lines
multiple lines can be traversed with backslashes

# commands


FROM Ubuntu:18.08    -> this creates the container os as ubuntu version 18.08. The version can be left off


LABEL version="0.1"  -> The label adds metadata to the image and is a key value pair
LABEL maintainer="A <a@amail.com>"
LABEL description="some description of the docker file"

WORKDIR /data   -> sets the working directory. If it doesnt exist it will be created. absolute paths only

RUN apt-get update && apt-get install -y \
python-pip \
python-dev \
python-numpy \
python-scipy

RUN pip install scikit-learn flask-restful

COPY ./model  -> copies from current directory into model directory 

EXPOSE 8080  -> opens port 8080 to make it accessible

ENV ml_debug_level=1   -> sets environment variables in container

ENV environment PRODUCTION  -> sets environment as production

CMD [ "python", "/model/classify_iris.py"]  -> runs python and passess as parameter the name of the script which has our model


# Example dockerfile 
the following is a dockerfile for the ml_classifier image. Anything in bold is commented out with hastag FYI

**start with base image**
FROM ubuntu

**set labels**
LABEL classifier_version="1.2"
LABEL charge_account="039303"
LABEL owner="A"
LABEL description="Basic iris classifier"

**instal libraries & packages**
RUN apt-get update && apt-get install -y \
python-pip \
python-dev \
python-numpy \
python-scipy \
python-pip

RUN pip install scikit-learn flask-restful

**copy model code from current directory**
COPY ./model

**expose the port for the api**
EXPOSE 8100

**set environment variables**
ENV ml_debug level=1
ENV environment PRODUCTION

**run the API**
CMD ["python", "/model/classify_iris.py"]


## building image
create a dockerfile, navigate to the dockerfile directory in #cmd and enter the following command:
docker build -t ml_example .

#-t refers to name. -t ml_example means the image is refered to as ml_example

. refers to current directory. I.e. docker image is built from dockerfile in current directory

# listing docker images on your system

open a #cmd and type:
docker images

This will show all available images

# running a docker image

open a #cmd and enter the command:

docker run -it ml_example

#-it refers to running interactively and the name of tag is ml_example


# exiting an image
open a #cmd and type:
exit()

This exits out the image