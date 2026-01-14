# FROM node:20-bullseye

# WORKDIR /app

# COPY package*.json ./

# RUN npm install --production

# COPY . .

# # COPY serve.json .
# #ARG VITE_BACKEND_URL
# #ENV VITE_BACKEND_URL=$VITE_BACKEND_URL
# RUN npm run build

# # Serve production build using a lightweight server
# RUN npm install -g serve

# EXPOSE 3000
# # CMD ["serve", "-s", "dist", "-l", "3000"]
# CMD ["npm", "start"]
FROM node:20-bullseye AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:20-alpine
WORKDIR /app
RUN npm install -g serve
COPY --from=build /app/build ./build
EXPOSE 3000
CMD ["serve", "-s", "build", "-l", "3000"]
