FROM node:16-alpine 

WORKDIR /app

# Copying package.json because npm install requires this json file.
COPY package.json .

# Moving the RUN npm install here because we don't want this to rebuild
RUN npm install

COPY . .



EXPOSE 4000

CMD [ "node", "app.js" ]



