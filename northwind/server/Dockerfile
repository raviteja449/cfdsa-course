# use the mode image
FROM node:14

# env variables for application
ENV APP_DIR=/app APP_PORT=3000

# for database
ENV DB_USER=root DB_PASSWORD=changeit

# change directory to $APP_DIR
WORKDIR ${APP_DIR}

ADD main.js .
ADD package.json .
ADD package-lock.json .

ADD config config
ADD public public
ADD views views

# install the dependencies
RUN npm install

## RUN 
#HEATHCHECK
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3  \
    CMD curl -f -s http://localhost:${APP_PORT}/health > /dev/null || exist 1

# the port the application is exposing
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT ["node", "main.js"]

