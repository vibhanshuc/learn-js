---
author: Vibhanshu Chaturvedi
authorURL: https://twitter.com/vibhanshu86
authorFBID: 901405709933351
title: Cypress Basics
---

# Basics of Cypress

## Install/Configure Cypress

1. To add cypress in the project

``` bash
npm install --save-dev cypress
```

1. To initialize cypress and open test runner

``` bash
npx cypress open
```

It will add following files in the root directory of the project

    .
    |-- cypress
    |   | -- fixtures/
    |   | -- integration/
    |   | -- plugins/
    |   | -- support/
    |-- cypress.json

1. To add eslint configurations for cypress

``` bash
npm i -D eslint-plugin-cypress
```

And add the plugin into `.eslintrc`

``` javascript
plugins: ['eslint-plugin-cypress'],
env: {
    'cypress/globals': true
}
```

1. Add following entries in `.gitignore`

``` text
cypress/screenshot
cypress/videos
```

## Write a Test

1. Create a file inside `cypress/integration` folder
