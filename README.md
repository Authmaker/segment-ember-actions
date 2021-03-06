[![Code Climate](https://codeclimate.com/github/Authmaker/segment-ember-actions/badges/gpa.svg)](https://codeclimate.com/github/Authmaker/segment-ember-actions)[![Build Status](https://travis-ci.org/Authmaker/segment-ember-actions.svg?branch=master)](https://travis-ci.org/Authmaker/segment-ember-actions)
# Require all action functions in Ember to have at least one analytics.track function call (segment-ember-actions)

This rule generates warnings for Ember action handler functions that do not have a call to analytics.track()

## Usage
To install:
```
npm install --save-dev eslint eslint-plugin-segment-ember-actions
```
add these to your `.eslintrc` file:
```
"rules": {
  "segment-ember-actions/analytics-track": 2
},
"plugins": [
  "segment-ember-actions"
]
```
and then run the **local** eslint:
```
node_modules/.bin/eslint app/**/*.js
```

## Rule details

The following controllers throw warnings:

```js
import Ember from 'ember';
export default Ember.Controller.extend({
  actions: {
      exampleAction() {}  
  }
});
```

The following controllers do not throw warnings:

```js
import Ember from 'ember';
export default Ember.Controller.extend({
    actions: {
        exampleAction() {
            analytics.track('something', {with: 'data'});
        }
    }
});
```

```js
import Ember from 'ember';
export default Ember.Controller.extend({
  actions: {
      //to-track
      exampleAction() {}  
  }
});
```
