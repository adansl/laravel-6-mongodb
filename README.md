## Laravel 6 + Docker + MongoDB

This is a fresh install of Laravel that includes a docker environment with MongoDB, Redis and Mongo Express. 
It has XDebug configured out of the box to work with PHPStorm. The [Laravel MongoDB Package](https://github.com/jenssegers/laravel-mongodb) is included too.

## Usage

You need to install Docker and Docker compose.

- Clone the repository
- Copy ```.env-example``` to ```.env```
- Run ```docker-compose up```
- Get inside the php container ```docker exec -it php sh```
- Run ```composer install```
- Generate the Laravel APP_KEY with ```php artisan key:generate```

After that, you'll have running the 

- **nginx** - `:8080`
- **MongoDB** - `:3306`
- **Mongo Express** - `:8888`
- **php** - `:9000`
- **XDebug Listening Port** - `:10000`

I included composer inside php container, to run npm scripts you can use
- `docker-compose run --rm npm run dev`

## .env 

These are the credentials for the root user of MongoDB, make sure they're the same for ```DB_USERNAME``` and ```DB_PASSWORD``` 
so Laravel can connect to the database. You can create another user for Laravel and keep your root user safe.

```
MONGO_ROOT_USER=root
MONGO_ROOT_PASSWORD=example
```

These are the credentials for login into [Mongo express](https://github.com/mongo-express/mongo-express) at ```localhost:8888```
```
MONGOEXPRESS_LOGIN=dev
MONGOEXPRESS_PASSWORD=dev
```

## Use Homestead

If you don't want to use Docker, you can use homestead instead, the steps are:

- Clone the repository
- Copy ```.env-example``` to ```.env```
- Copy ```Homestead.yaml.example``` to ```Homestead.yaml```
- Modify ```Homestead.yaml``` and specify your project path
- Run ```vagrant up```
- Wait it to finish and run  ```vagrant ssh```
- Run ```cd code```
- Run  ```composer install```
- Generate the Laravel APP_KEY with ```php artisan key:generate```
- Go to http://192.168.10.10/



## Contributing

Any improvement comment would be awesome, I'm very new in the Docker and DevOps world.

## Credits

I used some of the recipe of [aschmelyun/docker-compose-laravel](https://github.com/aschmelyun/docker-compose-laravel).
