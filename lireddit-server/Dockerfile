FROM node:14

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied.
#explation: https://dev.to/dimitrisnl/comment/ah9f#:~:text=This%20is%20used%20to%20download,app%20needs%20inorder%20to%20run.
COPY package.json ./
COPY yarn.lock ./

RUN yarn

COPY . .
# COPY .env.production .env no need as heroku sets it

RUN yarn build

ENV NODE_ENV production
# node_env is variable used by node.js to know whether this is in prod or development and we are setting it to prod in container

EXPOSE 8080
# this is just a declaration to the person running the container about which port the server listens on

CMD [ "node", "dist/index.js" ]
USER node

# process.env gives access to variables stored in node.js