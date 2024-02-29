FROM ubuntu:latest

# By default, listen on port 8081
EXPOSE 8081/tcp
ENV FLASK_PORT=8081

# Set the working directory in the container
WORKDIR /projects
RUN apt-get update && apt-get install -y git 
RUN apt-get install -y git-svn
# Copy the content of the local src directory to the working directory
COPY . .

# Install any dependencies
RUN \
  if [ -f requirements.txt ]; \
    then pip install -r requirements.txt; \
  elif [ `ls -1q *.txt | wc -l` == 1 ]; \
    then pip install -r *.txt; \
  fi
# Give ownership and permissions to the user
RUN chown -R user:user /projects
RUN chmod -R 755 /projects

# Specify the command to run on container start
CMD [ "python", "./app.py" ]
