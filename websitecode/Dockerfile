FROM ubuntu:20.04
RUN apt-get update && apt-get install -y tzdata && apt install -y python3.8 python3-pip git
RUN apt install python3-dev libpq-dev nginx -y
RUN mkdir /app
ADD ./requirements.txt /app
RUN pip install -r /app/requirements.txt
RUN mkdir /git
WORKDIR /git
RUN git clone https://github.com/kortiz001/plantwebsite.git
RUN mv /git/plantwebsite/websitecode/* /app/
RUN rm -rf ./plantwebsite
WORKDIR /app
EXPOSE 8000
CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangokubernetesplantwebsite.wsgi"]