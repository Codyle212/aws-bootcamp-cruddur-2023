FROM node:16.18

WORKDIR /frontend-react-js
ENV PORT=3000

COPY package.json .
RUN npm install

COPY . .

EXPOSE ${PORT}
CMD ["npm", "start"]