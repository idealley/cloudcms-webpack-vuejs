# Vue + Cloud CMS

[![Greenkeeper badge](https://badges.greenkeeper.io/idealley/cloudcms-webpack-vuejs.svg)](https://greenkeeper.io/)
Getting started Vue.js project with Cloud CMS.

* Server side rendered
* Hot reload
* API proxy
* Unit tests example

This example setup builds on the tutorial [how to manage menus with cloud CMS](https://idealley.gitbooks.io/cloud-cms-how-to-manage-menus/), it makes use of this [Cloud CMS proxy API example](https://github.com/idealley/cloudcms-proxy-api)

## Getting started

```bash
# Clone this repository
git clone https://github.com/idealley/cloudcms-webpack-vuejs.git cloudcms-vuejs

# Clone the Cloud CMS API proxy example
cd cloudcms-vuejs
git clone https://github.com/idealley/cloudcms-proxy-api.git api
```

### Build Setup

``` bash
# install dependencies
npm install

# install dependencies for the backend API
cd api
npm install
```
## Setup
The setup of Cloud CMS is handled by a CLI. You need to provide API Keys. If you do not have any [check the documentation](https://www.cloudcms.com/apikeys.html).

```bash
# add a gitana.json file (Cloud CMS apikeys)
touch gitana.json
vim gitana.json #paste and save (:wq)

# if you did not follow the above mentioned tutorial
node setup
# select "Setup Cloud CMS for the tutorial

# run the setup again
node setup
#select the second option "Import sample content"
# Add the needed relations: https://idealley.gitbooks.io/cloud-cms-how-to-manage-menus/content/adding-relations.html

# start the server
node app # nodemon app 

# come back in the vuejs folder
cd ..

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```
### Production
Serve the `dist/index.html` file over `http` (on apache, nginx, githubpages, ...)

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
