# Assessment

## Start docker

From within the project folder:
```
./vendor/bin/sail up -d
```

## Sail commands

Sail is a command meant to simplify running commands within the docker container.
Run the following commands if setting up for the first time:

```
./vendor/bin/sail artisan migrate
```

## Tasks

Complete the following tasks. Allow for two hours.

* create a table called `products`, with fields including `name` and `code`
* seed the table with arbitrary product records
* create an API endpoint to return a list of `products` ordered by `code`, in JSON format
* add the ability to filter products based on `name` and/or `code`, using the `q` parameter
