---
layout: post
title: Setting Up Rails Development Environment with Docker Compose
description: 
categories:
  - Tech
tags:
  - Container
  - Docker
  - Rails
  - Ruby
---

Hi folks! This guide is mostly written for participants of Go-Jek x BNCC bootcamp. But anyone who wishes to know how to setup his/her Rails development environment with Docker Compose is welcome as well. Just note that some examples here are specific to the sources I use for the bootcamp.

Since this guide is aimed at students who might be not familiar yet with containers in general, let me explain in a brief what containers are. Containers are a method of operating system virtualization that allow us to run an application and its dependencies in isolation within our actual operating system on our machine (be it a laptop, desktop, or some remote hosted server). Docker is one of container platform tools that we can use to build and manage containers. 
Lastly, Docker Compose is a tool for defining and running multi-container Docker applications.

You probably now have more questions than answers after reading the paragraph above. That is fine. In fact, that is great. If you are curious about container technology, you can read more about it in [this post](https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b).

## Prerequisite

1. Install Docker on Your Machine

     Since you are likely have different machines and operating systems (MacOS, Linux, Windows), I would rather you take a look at [Docker official documentation](https://docs.docker.com/install/) and try to install it by following the guideline there on your own.

## Setup

1. Create Dockerfile

     In your working directory, create a file named `Dockerfile` and fill it with:

     ```
     FROM ruby:2.5
     RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
     RUN mkdir /bncc
     WORKDIR /bncc
     COPY Gemfile /bncc/Gemfile
     COPY Gemfile.lock /bncc/Gemfile.lock
     RUN bundle install
     COPY . /bncc
     ```

     Just note that you can use replace `bncc` with any directory name that you want.

2. Create Initial Gemfile

     Now, create a file named `Gemfile` and fill it with:

     ```
     source 'https://rubygems.org'
     gem 'rails', '5.0.2'
     gem 'public_suffix', '~> 3.0.2'
     ```

     This will install required gems specific to our workshop requirements (Rails version 5.0.2).

3. Create Gemfile.lock

     Create a file named `Gemfile.lock` and leave it empty for the time being.

4. Create `docker-compose.yaml`

     Create a file named `docker-compose.yaml` and fill it with:

     ```
     version: '3'
     services:
       db:
         image: postgres
         volumes:
           - ./tmp/db:/var/lib/postgresql/data
       web:
         build: .
         command: bundle exec rails s -p 3000 -b '0.0.0.0'
         volumes:
           - .:/bncc
         ports:
           - "3000:3000"
         depends_on:
           - db
     ```

     Don't forget to replace `bncc` with the name of directory that you use in Step 1.

5. Build The Project

     Run this command:

     ```
     docker-compose run web rails new . --force --database=postgresql
     ```

     **ONLY FOR LINUX USERS:** If you run the previous command in Linux, there is a good chance that your newly created files are created with `root` account by Docker. You need to change them to regular files by running the following command:

     ```
     sudo chown -R $USER:$USER .
     ```

     Now this part is for everyone again, run the following command:

     ```
     docker-compose build
     ```

     It may take some time as Docker needs to download and setup a lot of things for your development environment.

6. Modify Database Configuration

     Next, we need to change our `config/database.yml` file. Make sure your database configuration file has the following lines:

     ```
     default: &default
       adapter: postgresql
       encoding: unicode
       host: db
       username: postgres
       password:
       pool: 5

     development:
       <<: *default
       database: bncc_development

     test:
       <<: *default
       database: bncc_test
     ```

7. Boot The App

     Once the previous command is finished, you can boot your app with:

     ```
     docker-compose up
     ```

     Afterward, we need to create the database. **Do the following command in the same folder but from a different terminal**:

     ```
     docker-compose run web rake db:create
     ```

     Now you should be able to see the Rails welcome page when you open `localhost:3000` from your browser.

## Usage

1. Find Your Container

     Now that you have Docker container up and running, you can get inside your container. First you need to know the name of your container. Find out with:

     ```
     docker ps
     ```

     The result should look something like this (you might need to scroll to the right):

     ```
     CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
     0e1bb4260f52        bncc_web            "bundle exec rails s…"   14 seconds ago      Up 13 seconds       0.0.0.0:3000->3000/tcp   bncc_web_1
     3bc7089f6ccd        postgres            "docker-entrypoint.s…"   8 minutes ago       Up 14 seconds       5432/tcp                 bncc_db_1
     ```

     In this case, the name of the container that we want to enter is `bncc_web_1`.

2. Enter The Container

     Run the following command:

     ```
     docker exec -it bncc_web_1 /bin/bash
     ```

     Don't forget to replace `bncc_web_1` with the actual name that you see as the result of your `docker ps` command.

     Now you can make changes to your Rails project from your host operating system while run terminal commands in your Docker `/bin/bash` environment.

3. Stop and Start

     To stop your app, run this command **in a different terminal from the one that runs your `docker-compose up`**:

     ```
     docker-compose down
     ```

     To start it again, you might have guessed it right by now:

     ```
     docker-compose up
     ```