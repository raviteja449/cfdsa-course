## building the image
# the environment is based on Node V14
FROM node:14

# creation of enviroement varibale to define my workspace
ENV APP_DIR=/app APP_PORT=3000

# crere and cd into APP_DIR 
# mkdir /app
# cd /app
WORKDIR ${APP_DIR}

# copy the file from fortune into /app
# Add local image
ADD main.js .
ADD package.json .
ADD package-lock.json .
# copy the directories
ADD public public
ADD views views

# install the dependencies - package.json
RUN npm install

## running the image
# Add healthcheck
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health > /dev/null || exit 1 

# the port the application is exposing
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT ["node", "main.js"]