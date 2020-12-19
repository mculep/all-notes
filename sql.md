# Setting up SQL

-   ```javascript
    npm i sequelize pg pg-hstore
    npm i --save-dev sequelize-cli
    npx sequelize-cli init
    ```

### ElephantSQL

-   _Create new instance_
-   _Name your file_
-   _Select Region_
-   _Keep at default_
-   _Click review (Make sure it's free)_
-   _Click instance_
-   _Click on name of instance to open up detail to put in config.json_

Go back to terminal and type in code .

-   _In terminal go to config.json_

-   _Change: "development in config.json"_

-   _password: with password from ElephantSQL (make sure it's in quotation)_

-   _database: "user & default database"_

-   _host: with server in ElephantSQL without the ( )_

-   _dialect: postgres ( Will always be postgres as long as you're working with postgres_)

-   ```javascript
    npx sequelize-cli model:generate --name yourmodelname --attributes name:string,type:string
    ```

    -   _Create a name and rename the attributes_

-   ```javascript
    npx sequelize-cli db:migrate
    ```
