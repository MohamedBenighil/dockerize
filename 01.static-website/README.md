# Prerequisite
- DOcker engine 

# quickstart
- Build the image: `docker build -t mbe .`
- Create an instance from it : `docker run -p 8080:80 --rm mbe`
- Make sure it is up and running: `docker ps`
- Open Chrome and navigate to `http://localhost:8080`