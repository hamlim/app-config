# App Config

App config is a standard for a universal config file that can be used to set static data for build tooling.

Think of it like a generic alternative to package.json

### Format

App Config should be named one of:

* `app.config.json` or `app.config.js`
* `app-config.json` or `app-config.js`
* `appconfig.json` or `appconfig.js`
* `.appconfig` (only parsed as json)

It can either be formatted as json, or a javascript file that exports a function that returns the config.

```json
{
  "meta": {
    "name": "App name",
    "repo": "github.com/hamlim/app-config"
  },
  "babel": {
    "preset": [
      [
        "@babel/preset-env",
        {
          "targets": {
            "browsers": ["last 2 versions", "safari >= 7"]
          }
        }
      ]
    ]
  },
  "ds": {
    "paths": {
      "numbers": "design-system/numbers.js"
    }
  }
}
```

Or as a javascript file:

```javascript
module.exports = function() {
  return {
    babel: {
      preset: [
        [
          '@babel/preset-env',
          {
            targets: {
              browsers: ['last 2 versions', 'safari >= 7'],
            },
          },
        ],
      ],
    },
    ds: {
      paths: {
        numbers: 'design-system/numbers.js',
      },
    },
  }
}
```

### Why?

As many critics have said, `package.json` is inconveniently named as config for your entire app when your resulting deliverable isn't a package for others to consume.

A generic json or javascript config file can be thought of as the entry point for applications. It stores configuration for build tooling, as will as basically anything else, the example above has some meta information about the app too.
