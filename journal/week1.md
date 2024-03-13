
# Week 1 — App Containerization
## working on App containerization
## Refrences 
### 1- install Docker extention for vscode
### 2- Dockerize the backend
```bash
pip install flask
pip install flask-cors
```
```bash
cd backend-flask
export FRONTEND_URL='*'
export BACKEND_URL='*'
python3 -m flask run --host=0.0.0.0 --port=4567 #install flask
cd .. 
```
- make sure to unlock the port on the port tab
- open the link for 4567 in your browser
- append to the url to /api/activities/home
- you should get back json
### 3- Add dockerfile to run flask but from dockerfile instead
check [Dockerfile](../backend-flask/Dockerfile)
```
FROM python:3.10-slim-buster
WORKDIR /backend-flask
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
ENV FLASK_ENV=development
EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
```

### 4- build the docker image for the backend

```bash
docker build -t  backend-flask ./backend-flask
```
#### 4.1 run the container from docker image
make sure that docker extention is installed 
```bash
docker run --rm -p 4565:4567 -d -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask

unset FRONTEND_URL="*"
unset BACKEND_URL="*"
```
