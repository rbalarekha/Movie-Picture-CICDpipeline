FROM public.ecr.aws/docker/library/node:18.14.2-alpine3.17

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}

WORKDIR /app
  
  # Copy dependency files
COPY package*.json ./
  
  # Install packages
RUN npm ci
  
  # Install serve globally to serve the React app
RUN npm install -g serve
  
  # Copy code
COPY . .
  
  # Build the app
RUN npm run build
  
  # Ensure build directory is readable and executable
RUN chmod -R 755 /app/build
  
  # Expose the port used by the React app
EXPOSE 3000
  
  # Start the React app when the container starts
CMD ["serve", "-s", "build"]