FROM node:25-2.1-slim AS build
ADD . /Node
WORKDIR /Node
RUN npm install && \
    npm run build

FROM nginx:1.29.3-alpine AS runtime
LABEL project="sample-script"
LABEL author="devopsteam"
COPY --from=build /Node/build /usr/share/nginx/html
EXPOSE 80
