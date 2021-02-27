# Monorepo concepts

## What is monorepo?

A monorepo is a single repository. A monolith is a massive codebase.

#### Monorepo vs Multirepo

A monorepo keeps everything in one repository. A multirepo (multiple repositories) typically has one repository for each project. The more projects, the more repositories. A multirepo is also known as polyrepo.

#### How do it?

-    Create a main root folder `mkdir foldername`
-    Entery on root folder `cd foldername`
-    Create a packages folder `mkdir packages`
-    Create a package.json file `touch package.json`
-    On package.json put the code bellow

```json
{
     "private": "true",
     "name": "mono-repo",
     "workspaces": ["packages/*"]
}
```

-    On package folder create a folder for each resource

#### example

On my case I created `api` folder for backend code and `web`for frontend one

-    On my `api` folder I created a `package.json` with the code bellow

```json
{
     "name": "@mono-repo/api",
     "version": "1.0.0",
     "description": "api backend",
     "main": "app.js",
     "author": "Alessandro",
     "license": "MIT",
     "private": false
}
```

Note On `name` I used conventional name with `@` referencing my main `package.json` on root folder

-    At `web`folder I created a `package.json`with the code bellow

```json
{
     "name": "@mono-repo/web",
     "version": "1.0.0",
     "description": "Site frontend",
     "main": "index.js",
     "author": "Alessandro",
     "license": "MIT",
     "private": false,
     "dependencies": {
          "@mono-repo/api": "1.0.0"
     }
}
```

-    On root folder run the command `yarn install` or `npm install`
-    On `web` folder run the command `yarn install` or `npm install` to install `api`resources

The most important is `dependencies` I am importing resources from my `api` folder
On my `api`I created an index.js with a simple exported function
On my `web`I created an index.js importing the `api` function

if you run the web index you will see that we can use api resources
