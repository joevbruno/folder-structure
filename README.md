A few thoughts on client-side folder structure in a large react / redux application






### Folder Structure

+ [Redux Folder Structure](https://github.com/rackt/redux/tree/master/examples/shopping-cart)
+ React Component in [React Toolbox](https://github.com/react-toolbox/react-toolbox/tree/dev/components/drawer)
+ [Angular reference]('./angular.pdf')

#### Assumptions

+ single Redux Store
+ single React Router
+ single bundle.js (?)
+ single styles.css (?)

Does allow for multiple JS bundles and multiple css files

```

v2/
+--actions 			                  // util to create redux actions 
+--assets
|  +-- *                             // globally used images
+--config
|  +-- api                           // api endpoints to hit for data
|  +-- components                    // core-ui config to include components ("wrappers")
|  +-- utils                         // core-utilz config for global utils like Actions, ActionTypes, request
+--containers
|  +-- devtools                      // redux devtools
|  +-- main                          // main 'layout file' that include nav, footer and app wrapper.
|  +-- root                          // Redux Provider + Routes
+--controls
|  +-- *                             // in-house global controls / wrappers around kendo
+--modules                           // sections of the app
|  +-- BaselineReview
|  +-- WBS Dashboard
|  +-- FinPlan Review
|  +-- Cost Module
|  +-- Inbox                         // each module repeats the basic redux folder stack
|      +-- actions                   // actions specific to inbox
|      +-- components                // smaller, mostly stateless components only found in inbox
|         +-- InboxCountCard
|             +-- index.jsx
|             +-- _style.scss
|      +-- containers                // stateful wrappers around react components that connect to Redux stores and Router
|      +-- reducers                  // reducer or reducers 
|      +-- routes                    // routes for Inbox modules
|      +-- _style.scss               // imports _styles from all / some components and containers in that module
|  +-- Annoucements
|  +-- _main.scss
+--reducers                          // combine reducers
+--routes                            // combine routes
+--scss                              // ITCSS stack 
|  +-- 01-config                     // fonts, icons, images, vendor css or scss (not NPM or Bower installed)
|  +-- 02-utils                      // variables, functions, placeholders, mixins
|  +-- 03-generic                    // normalize.css
|  +-- 04-base                       // base default styles, print.css
|  +-- _main.scss
|  +-- 07-overrides
+--stores
+--utils

+--main.scss                         // includes scss/main.scss then controls, modules styles, and finally trumps/overrides
+--app.js
+--index.html (.cshtml)
```