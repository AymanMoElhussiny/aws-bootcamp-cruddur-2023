# base image 
FROM python:3.10-slim-buster

# declear the start working directory
WORKDIR /backend-flask

# copy the depnencies from the working directory

COPY requirements.txt requirements.txt

# install flask and flask-cor

RUN pip3 install -r requirements.txt

# copy all of the application needed
COPY . .

ENV FLASK_ENV=development

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]