## Build
FROM beevelop/ionic:latest AS ionic

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# package.json and package-lock.json
COPY package*.json ./

# Clean and install dependencies
RUN npm ci

# Bundle app source
COPY . .

# Compiles web assets and prepares them for deployment
RUN ionic build

## Run 
FROM nginx:alpine

# COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html