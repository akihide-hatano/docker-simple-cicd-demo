FROM node:18 AS base
CMD [ "bash" ]

# Build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
ARG REACT_APP_API_SERVER
RUN npm ci && npm run build

# Hosting in nginx
FROM nginx:latest AS prodution
COPY --from=build /workspace/build /var/www
COPY nginx.conf /ect/nginx/cinf.d/default.conf
