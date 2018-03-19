FROM rhoar-nodejs/nodejs-8:latest

COPY package.json /opt/app-root/src/
COPY nodejsActionBase/* /opt/app-root/src/
COPY nodejsActionBase/src /opt/app-root/src/src

RUN npm install \
  && npm cache clean --force

CMD ["node", "--expose-gc", "app.js"]
