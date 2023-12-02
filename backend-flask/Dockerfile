FROM python:3.10-slim-buster
#Setting a folder for further command execution, all commands running afterward will be from this directory
WORKDIR /backend-flask

#Copying over dependencies file for backend application 
COPY requirements.txt .
#Installing dependencies from with pip
RUN pip3 install -r requirements.txt
#Copying over everything from the directory the Dockerfile is located to working directory inside container
COPY . .
#Setting up Environmental variable for Backend
ENV FLASK_ENV=development
#Export Port for connection
EXPOSE ${PORT}
# running the flask application
CMD ["python3","-m","flask","run","--host=0.0.0.0","--port=4567"]
