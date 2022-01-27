# syntax = docker/dockerfile:1.3
#Install dependencies (no compilation)
FROM python:3.6-alpine as build
WORKDIR /code
COPY ./k8s-mastery/sa-logic/sa/requirements.txt .
RUN --mount=type=cache,target=~/.cache/pip  pip3 install -r requirements.txt && \
    python3 -m textblob.download_corpora

#run app 
FROM build as runner 
WORKDIR /code
# copy source code from host (not from stage)
COPY ./k8s-mastery/sa-logic/sa .
ENTRYPOINT ["python3"]
CMD ["sentiment_analysis.py"]
