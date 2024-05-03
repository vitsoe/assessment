# Assessment

## Git Setup

Please do not fork the repository. You will need to create a copy of the repository in your own
Github account. To achieve this, do the following:

* Create a new repository in your own Github account
* Clone this assessment repository to your local machine
* Clone your new repository to your local machine
* Remove the `.git` folder from the Vitsoe assessment project folder
* Move the `.git` folder into the local Vitsoe assessment project folder
* `git status` will now show a number of new files, copied from the Vitsoe assessment project
* Add, commit, and push these files to your own repository
* Give read access to your new repository to the following Github accounts:
  * `swoodvitsoe`
  * `tcrawford-vitsoe`

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

If you have time:
* add throttling to the API with configuration stored in `config/`
