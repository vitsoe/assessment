# Assessment

This is a public repository intended to assess a person's development ability.
Requirements:
* a working knowledge of PHP & Laravel
* docker desktop installed
* four hours of focused time
* a timer

Please only spend four hours working on the assessment and see how
far you get.
If you spend more than four hours, we won't be able to make a fair assessment
of your skills.
You should start the timer once the docker containers have successfully started, e.g. you see this in your terminal:

```
➜  assessment git:(main) ✗ vendor/bin/sail up -d
[+] up 7/7
 ✔ Network assessment_sail            Created   0.0s
 ✔ Container assessment-redis-1       Started   0.3s
 ✔ Container assessment-mariadb-1     Started   0.3s
 ✔ Container assessment-selenium-1    Started   0.2s
 ✔ Container assessment-mailpit-1     Started   0.2s
 ✔ Container assessment-meilisearch-1 Started   0.3s
 ✔ Container assessment               Started   0.4s
```

## Git Setup

Please do not fork the repository. You will need to create a copy of the repository in your own
GitHub account. To achieve this, do the following:

* Create a new repository in your own GitHub account
* Clone your new repository to your local machine
* Clone this assessment repository to your local machine
* Remove the `.git` folder from the Vitsoe assessment project folder
* Move the `.git` folder (from your own newly created project) into the local Vitsoe assessment project folder
* `git status` will now show a number of new files, from the Vitsoe assessment project
* Add, commit, and push these files to your own `main` branch of your repository
* Create a branch off `main` which will contain your assessment submission
* Once you have spent four hours working on the assessment, push your changes to the appropriate branch, and then create *two pull requests*
* Please add any notes or comments to your pull requests; a pull request is important, as it makes reviewing your code changes easier
* Give read access to your new repository to the following GitHub accounts:
  * `JamesGawthorpe`
  * `tcrawford-vitsoe`
  * `sgeorgiou-vitsoe`

## Installation steps

### Composer install and sail

To have access to the `sail` commands, you need to run `composer install` on your host.
Sail is a command meant to simplify running commands within the docker container.
Please refer to https://getcomposer.org/download/ for downloading and installing composer.
From within the `assessment` folder, run:
```
composer install
```

### Create .env from .env.example

You will need a `.env` file which is ignored by Git and should not be committed.
Copy `.env.example` to `.env`, uncomment all the `DB_*` settings, and add a root password
To find a valid value for `WWWUSER` and `WWWGROUP`, use `id` in a terminal.
Set `WWWUSER` to the value of `uid`, and `WWWGROUP` to the value of `gid`.

### Start docker

From within the project folder:
```
./vendor/bin/sail up -d
```

### Laravel setup

Run the following commands to create tables and generate `APP_KEY`:

```
./vendor/bin/sail artisan migrate --force
./vendor/bin/sail artisan key:generate
```

You should now be able to open http://localhost/ and see the default Laravel welcome page

## Tasks

Assume no authentication is required.
Complete the following tasks while considering security and flexibility.
Create one branch for `Task one` and a second branch for `Task two`

### Task one

* create a table for products, with at least the fields: `name`, `code`, `internal_notes`
* create a table for categories, with at least the fields: `cateogry`
* seed the products table with arbitrary products
* seed the categories table with arbitrary categories
* create model classes for products and categories, allowing for a product to be associated to multiple categories, i.e. a product can have many categories, and a category can be associated with many products
* create an API endpoint to return a list of products ordered by `code`, in JSON format
* utilise response shaping to return the search results, `internal_notes` should not be exposed to the end user
* add the ability for the user to supply a `q` parameter which will be matched against `name`, `code`, or `category`
* ensure API input parameters are validated

### Task two

Create a branch off `Task one` branch, and add the following improvements to it:

* create admin endpoints to add/remove products
* create admin endpoints to add/remove categories
* add throttling to the API with configuration stored in `config/`
* add pagination to the API results

### Nice to have

Products are synced into this system from an external source via a webhook. The external system may send
the same update more than once (e.g. after a timeout it didn't get confirmation for), and updates may not always arrive
in the order they were sent.

Add a webhook endpoint that accepts a product update and processes it idempotently: a repeated delivery of the same
update should not create a duplicate product or duplicate side effects, and a late-arriving, older update should not 
overwrite a newer one. The state of the products on the local DB should be reflecting the state in the external system.
