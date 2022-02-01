FROM node as build
WORKDIR /code
COPY ./s3-uploader/package.json ./s3-uploader/package-lock.json  ./
RUN npm install
COPY ./s3-uploader .
#CMD [ "node","./server.js" ]
#CMD [ "sh", "-c", "while true; do sleep 3600; done" ]
#RUN npm run build
CMD [ "sh", "-c", "npm start" ]


