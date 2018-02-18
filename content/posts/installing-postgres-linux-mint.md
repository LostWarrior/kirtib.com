---
author: "Kirti Bhardwaj"
date: 2018-02-17
linktitle: Install Postgres On Mint
prev: /posts/building-site-with-hugo
title: Installing Postgres on Linux Mint
weight: 10
---

## Background

Recently I needed to install and setup Postgres on my system for a side project. Here are the steps I followed to get it working on my machine.

```
## Check For Version Installed:
lsb_release -a
It will give you and output like this.
```

![OS Release](/images/release.png)  

Once this is done we run:

```
$ sudo apt-get update
$ sudo apt-get install postgresql postgresql-contrib
```
Click enter when prompted.

Postgres uses ``` "roles"``` to handle authorization.

Switch to Postgres prompt :

```
sudo -u postgres psql
```
To exit the prompt, you use:

```
\q or, Control + D
```

So, now we have a postgres role configured in our database. We can create new roles

```
sudo -u postgres createuser --interactive
```

It will prompt you:
```
Enter name of role to add: test
Shall the new role be a superuser? (y/n) y/n
```

We need to set up as password:

```
sudo -u postgres psql postgres
Enter your password twice.
```

To check what users are there, from outside the prompt:
```
psql postgres -tAc "SELECT * FROM pg_roles"
```

or from inside the prompt:
```
SELECT * FROM pg_roles
```
Another assumption postgres makes is that there will be a databse with same name as the role used for login. So we create a new databse:

```
From inside the postgres db:
createdb test
From outside:
sudo -u postgres createdb test
```

To login as the user:
```
sudo -u test psql
```

If you want your user to connect to a different database:

```
psql -d dbName
```
To check connection information:

```
test-# \conninfo
```

You can also install pgAdmin III, it is essential if you are a beginner:

```sudo apt-get install pgadmin3```

Sometimes, you will get an error :
```
1. psql: FATAL : database "name" does not exist

To solve this, you have to create a new database with the name that you are using to login

2. sudo: unknown user: test
   sudo: unable to initialize policy plugin

To solve this, you have to add a matching linux user:

sudo adduser test

```

That's it for now, you can go on ahead and create a few tables.That deserves another post of its own.
