FROM python:3

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install git

RUN git clone https://github.com/macrat/BlankGenerator.git /usr/local/share/blankgenerator
RUN cd /usr/local/share/blankgenerator && pip3 install -r requirements.txt
RUN pip3 install pyinotify

RUN mkdir /source /destination
RUN useradd generator
RUN chown generator:generator /usr/local/share/blankgenerator /source /destination

USER generator
WORKDIR /usr/local/share/blankgenerator

CMD python3 ./main.py /source -o /destination
