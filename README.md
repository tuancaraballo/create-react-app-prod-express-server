# create-react-app-prod-express-server

Basic create-react-app module + express servver for backend for future boiler plate

1- Create a new folder (mkdir folder_name)
2- Initialize package.json  ( npm init -y )
3- Add server file ( touch server.js)
4- Add entry point to package.json  ("start": "node server.js")
5- Install express and other modules ( npm install express --save)
6- Create git file:
    $ git init
    $ echo node_modules > .gitignore
    $ git add .
    $ git commit -m "Initial commit"
7- Push it to remote repo if you need it.
8- Create heroku app  ( heroku create)
9- Create react app boilerplate (create-react-app client) this will create the react app inside the client folder
10- Add a proxy to client/package.json ("proxy": "http://localhost:5000")
11- Tell heroku to build the app in client/build after we have push it to heroku
    - Inside the expreess package.json add this :
        "scripts": {
             "start": "node server.js",
            "heroku-postbuild": "cd client && npm install --only=dev && npm install && npm run build"
         }
--> This tells Heroku “hey, after you’re done doing what you do, go into the client folder and build my React app.”
--> Calling npm install twice is not a mistake: by default, npm install will skip “devDependencies”, but we need those
because “react-scripts” is in there, and the npm install --only-dev command installs those devDependenices.
We also need the production “dependencies” so that’s why we run npm install a second time.
12- Add, commit and push to git and heroku

13- Consider adding "npm prune --production" aget npm run build, this will remove the unneccessary dev dependencies after
the build is complete.
      "scripts": {
             "start": "node server.js",
            "heroku-postbuild": "cd client && npm install --only=dev && npm install && npm run build && npm prune --production"
         }
