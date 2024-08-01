# Assessment

This is a public repository intended to assess a person's development ability.
Requirements:
* a working knowledge of PHP & Laravel
* docker desktop installed
* four hours of focused time
* a timer

Please only spend four hours working on the assessment, and see how
far you get.
If you spend more than four hours, we won't be able to make a fair assessment
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
* Move the `.git` folder (from your own newly created project) into the local Vitsoe assessment project folder
* `git status` will now show a number of new files, from the Vitsoe assessment project
* Add, commit, and push these files to your own main repository branch
* Create a branch which will contain your changes
* Once you have spent four hours working on the assessment, push your changes to the branch, and then *create a pull request*
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

* create a table for products, with at least the fields: `name`, `code`, `internal_notes`
* create a table for categories, with at least the fields: `cateogry`
* seed the products table with arbitrary products
* seed the categories table with arbitrary categories
* create model classes for products and categories, allowing for a product to be associated to multiple categories, i.e. a product can have many categories, and a category can be associated with many products
* create an API endpoint to return a list of products ordered by `code`, in JSON format
* utilise response shaping to return the search results, `internal_notes` should not be exposed to the end user
* add the ability for the user to supply a `q` parameter which will be matched against `name`, `code`, or `category`
* ensure API input parameters are validated

If you have time:

* create admin endpoints to add/remove products
* create admin endpoints to add/remove categories
* add throttling to the API with configuration stored in `config/`
* add pagination to the API results
