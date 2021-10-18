# Tutorial: Deploying a basic Saber app on Jekyo

Demo app [here](https://saber-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin 
Your email?: **************
Your password?: **********
You have successfully signed in!
```
If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`. 

## 1. Create a basic Saber app

You can start your Saber project by using `jekyo create`

Using the **arrows** on your keyboard, select **saber** and press **enter**.  
```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)     
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/) 
❯ saber A basic starter app using [Saber](https://saber.land/)
```
When prompted, enter the desired name for your Saber app. 

`Application name?: saber-tutorial`

This will create a basic Saber app in the current directory by cloning this [Saber starter app](https://github.com/jekyo/saber-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Saber app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd saber-tutorial`

Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://saber-tutorial.jekyo.app ... OK
```

You can now browse to your Saber app on https://saber-tutorial.jekyo.app (replace 'saber-tutorial' with your app name)

## 2. Deploying an existing Saber app

Navigate to your local Saber app directory

`cd my-saber-app`

Initialize a git repository if you haven't already done so by running `git init`. 

### Edit package.json

Make sure you include `$PORT` and `$HOST`:

```
"scripts": {
   "dev": "saber --port $PORT --host $HOST",
   "build": "saber build",
   "start": "npm run build && npm run dev"
},
```
Also your theme should be added as a dependency: 

```
"dependencies": {
    "saber": "^0.11.7",
    "saber-theme-minima": "^3.2.2"
  }
```


### Create an empty Jekyo app:

`jekyo create` 

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory. 

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app: 

`Application name?: my-saber-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-saber-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-saber-app
```
### Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-saber-app.jekyo.app ... OK
```

You can now browse to your Saber app on https://my-saber-app.jekyo.app (replace 'my-saber-app' with your app name)

## Pushing local changes to Jekyo 

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while. 