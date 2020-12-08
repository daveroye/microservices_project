## Build
FROM beevelop/ionic AS ionic

# Create the application directory
WORKDIR /usr/src/app

# We can use wildcard to ensure both package.json AND package-lock.json are considered
# where available (npm@5+)
COPY package*.json ./

# Install the application dependencies
RUN npm ci

# Bundle app source
COPY . .
RUN ionic build

## Run 
FROM nginx:alpine
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html
