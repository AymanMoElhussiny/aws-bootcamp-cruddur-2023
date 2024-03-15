
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
```

you can test the backend using the below 
```bash
curl -X GET http://localhost:4565/api/activities/home -H "Accept: application/json" -H "Content-Type: application/json"
```
### 5- Containerize the frontend
### 5.1 run NPM install
since NPM is need to be installed before building the container since it needs to COPY the content of node_modules 
```bash
cd frontend-react-js
npm i
```
### 5.2 create dockerfile fore frontend 
check [Dockerfile](../frontend-react-js/Dockerfile)
```
FROM node:16.18
ENV PORT=3000
COPY . /frontend-react-js
WORKDIR /frontend-react-js
RUN npm install
EXPOSE ${PORT}
CMD ["npm", "start"]
```
### 5.3 Build the container 
```
docker build -t frontend-react-js ./frontend-react-js
```
### 5.4 Run the Container
```
docker run -p 3000:3000 -d frontend-react-js
```
### 6 Update the api for notification
