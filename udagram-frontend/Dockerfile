### Build Stage
FROM node:16 AS build

# Install Ionic CLI
RUN npm install -g @ionic/cli

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package.json ./
RUN npm install --force

# Bundle app source
COPY . .

# Build the Ionic project
RUN ionic build

### Run Stage
FROM nginx:alpine

# Copy the built app to the nginx container
COPY --from=build /usr/src/app/www /usr/share/nginx/html
