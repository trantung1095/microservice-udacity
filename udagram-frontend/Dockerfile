# Use IONIC base image
FROM beevelop/ionic:latest AS ionic

# Create app directory in Docker
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies in Docker
RUN npm install --force

# Copy app from local environment into the Docker image
COPY . .

# Build app
RUN NODE_OPTIONS=--openssl-legacy-provider ionic build

FROM nginx:alpine

#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html