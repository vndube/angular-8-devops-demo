FROM node:12.16.1-alpine As builder

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm config set registry http://docker.for.win.localhost:8085/repository/npm-group/
#RUN npm config set registry http://docker.for.win.localhost:8085/repository/npm-group/_auth=a5dd0bd3-1cce-39c8-bf43-ea043e3a25bd
#RUN npm config set loglevel verbose

RUN npm install

COPY . .

RUN npm run build --prod

FROM nginx:1.15.8-alpine

COPY --from=builder /usr/src/app/dist/angular-8-example-app/ /usr/share/nginx/html
