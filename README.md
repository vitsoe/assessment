# Assessment

This is a public repository intended to assess a person's development ability.
Requirements:
* a working knowledge of PHP & Laravel
* docker desktop installed
* two hours of focused time
* a timer

Please only spend two hours working on the assessment, and see how
far you get.
If you spend more than two hours, we won't be able to make a fair assessment
of your skills.
You should start the timer once the docker containers have successfully started, e.g. you see this in your terminal:

```
➜  assessment git:(main) ✗ sail up -d
[+] Running 6/6
 ✔ Container assessment-selenium-1      Started                                                  
 ✔ Container assessment-meilisearch-1   Started
 ✔ Container assessment-redis-1         Started                                                  
 ✔ Container assessment-mailpit-1       Started                                                  
 ✔ Container assessment-mysql-1         Started                                                  
 ✔ Container assessment-laravel.test-1  Started                                                 
```

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
* Create a branch which will contain your changes
* Once you have spent two hours working on the assessment, push your changes to the branch, and then create a pull request
* Please add any notes or comments to your pull request - a pull request is import, as it makes reviewing your code changes far easier
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

Assume no authentication is required.
Complete the following tasks, while considering security and flexibility:

* create a table called `products`, with fields including `name`, `code`, `internal_notes`
* seed the table with arbitrary product records
* create an API endpoint to return a list of `products` ordered by `code`, in JSON format
* add the ability to filter products based on `name` and/or `code`, using the `q` parameter

If you have time:

* add throttling to the API with configuration stored in `config/`
* add pagination to the API results
