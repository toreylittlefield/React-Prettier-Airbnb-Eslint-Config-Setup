From [codeStryke](https://gist.github.com/codeStryke/fa456a8f05ac9b2ac4fba679a08858bc)

### package.json
```
{
  "engines": {
    "node": "8.11.3",
    "npm": "5.8.0"
  },
  "scripts": {
    "precommit": "lint-staged",
    "lint": "eslint '**/*.{js,jsx}'",
    "lint:fix": "eslint --fix '**/*.{js,jsx}'",
    "lint:debug": "DEBUG=eslint:cli-engine eslint '**/*.{js,jsx}'",
    "eslint-check": "eslint --print-config .eslintrc.json | eslint-config-prettier-check"
  },
  "lint-staged": {
    "linters": {
      "**/*.{js,jsx}": [
        "npm run lint:fix",
        "git add"
      ]
    }
  },
  "devDependencies": {
    "eslint": "^4.19.1",
    "eslint-config-airbnb": "^17.0.0",
    "eslint-config-prettier": "^2.9.0",
    "eslint-plugin-import": "^2.12.0",
    "eslint-plugin-jsx-a11y": "^6.0.3",
    "eslint-plugin-prettier": "^2.6.1",
    "eslint-plugin-react": "^7.10.0",
    "husky": "^0.14.3",
    "jest": "^23.2.0",
    "lint-staged": "^7.2.0",
    "prettier": "^1.13.6"
  }
}
```

### .eslintrc.json
```
{
    "env": {
        "browser": true,
        "jest": true
    },
    "parser": "babel-eslint",
    "extends": ["airbnb", "prettier/react","plugin:prettier/recommended"],
    "plugins": ["react", "prettier"],
    "rules": {
        "react/jsx-filename-extension": [1, {"extensions":[".js"]}],
        "prettier/prettier": "error"
    }
}
```
### .eslintignore
```
public/**
node_modules/**
coverage/**
src/registerServiceWorker.js
```
### .prettierrc
```
{
    "singleQuote": true,
    "tabWidth": 4
}
```