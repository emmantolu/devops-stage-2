# Use latest Node.js official image as base
FROM node:latest

# Set working directory
WORKDIR /app

# Copy all application files
COPY . .

# Install dependencies
RUN npm install

# Expose server port
EXPOSE 5173

# Run the development server
CMD ["npm", "run", "dev", "--", "--host"]
