FROM node:16.17.0

# Set working directory
WORKDIR /usr/src/app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl

# Install NPM global packages
RUN npm install -g create-next-app pm2

# Clone frontend repository from GitHub (with authentication)
RUN git clone https://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:x-oauth-basic@github.com/jassimalmathkour/housemade-frontend.git .

# Install frontend dependencies with --legacy-peer-deps
RUN npm install --legacy-peer-deps

# Start the frontend application
CMD ["npm", "start"]

