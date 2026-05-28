FROM node:20-bullseye

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    ffmpeg \
    imagemagick \
    webp \
    git \
    curl \
    python3 \
    build-essential \
    libglib2.0-0 \
    libnss3 \
    libnspr4 \
    libatk1.0-0 \
    libatk-bridge2.0-0 \
    libcups2 \
    libdrm2 \
    libdbus-1-3 \
    libxcb1 \
    libxkbcommon0 \
    libxcomposite1 \
    libxdamage1 \
    libxfixes3 \
    libxrandr2 \
    libgbm1 \
    libasound2 \
    && rm -rf /var/lib/apt/lists/*

# Copy package files first for better caching
COPY package*.json ./

# Install node dependencies
RUN npm install --production

# Copy the rest of the app
COPY . .

# Create sessions folder
RUN mkdir -p /app/sessions

# Expose port if you use a web server
EXPOSE 3000

# Start the bot
CMD ["npm", "start"]