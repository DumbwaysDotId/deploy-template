# Deploy backend to heroku

`Heroku` is a cloud platform as a service supporting several programming languages. One of the first cloud platforms, Heroku has been in development since June 2007, when it supported only the Ruby programming language, but now supports Java, Node.js, Scala, Clojure, Python, PHP, and Go.

- Install postgres

  ```text
  npm install pg
  ```

* On server side, create `Procfile` file & add code below

  ```text
    release: node_modules/.bin/sequelize db:migrate; node_modules/.bin/sequelize db:seed:all;

    web: node index.js
  ```

* Modify the server port from env, file: `server/index.js`

  ```javascript
  ...
  const port = process.env.PORT || 5000;
  ...
  ```

* Setup config `production`, file : `server/config/config.json`

  ```json
  ...
  "production": {
   "use_env_variable": "DATABASE_URL",
   "dialect": "postgres",
   "protocol": "postgres",
   "dialectOptions": {
     "ssl": {
       "require": true,
       "rejectUnauthorized": false
     }
   }
  }
  ...
  ```

* Go to Heroku web : [Link](https://www.heroku.com/) & Create new app

* Fill out the form → click `Create app`

* Go to Resources → add `Heroku Postgress` on Add-ons

* Create repository on github & push restAPI project

* On heroku, Go to `Deploy` → Search repository & click `connect`

* Scroll down, click `Enable Automatic Deploys`, Choose a branch & click `Deploy Branch`

* Go to `Settings`, scroll down to `Config Vars`, Add the `config vars` from dotenv file

  ![image](https://raw.githubusercontent.com/DumbwaysDotId/deploy-template/1.Deploy-backend-to-heroku/img.png)

* Then to ensure our Backend is deployed, we can click `Open App`
