# whether-weather-better

https://whether-weather-better.herokuapp.com/

My first work with using the Vue.js Framework to create a simple single page app that is automatically updated via an API call.

The app compares the current and forecast temperature across three locations (where family are) and determines where it is warmest currently and where it is forecast to be warmest.

The app updates the values every 30 minutes and re-runs the comparison.

It gets the weather data from an intermediary API I also built, that can be found at this [repo](https://github.com/andygnewman/whether-weather-api).

I used the 'scaffolded' Vue, so at some stage would like to strip out all the unnecessary elements.

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
