# Visual Studio Code - ESLint, Prettier, JSConfig & Airbnb Setup For JS / React Projects
---

## This document outlines a setup for React projects in VS Code. 

### Implements the following: 
- Linting rules using [Airbnb style guide](https://airbnb.io/javascript/react/) & [ESLint](https://eslint.org/)
- Formatting code with the [Prettier Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- Using absolute paths/imports with [jsconfig.json](https://code.visualstudio.com/docs/languages/jsconfig)

#### Notes & Info
The following installation & setup guide is for the `create-react-app` and are only tested using it and not on other React app configurations. 

- More advanced configurations of webpack & babel are possible but are not included in this guide.

- These guide uses `npm` as installation, although you can use YARN but commands are not provided.


---
## 📝 Table of Contents

- [Quick Start](#quick-start)
- [ESLint](#eslint)
- [Airbnb Styles](#airbnb)
- [Prettier](#prettier)
- [Absolute Paths For Imports](#abs-paths)
- [Tutorials & Resources](#tutorials)

---

## Dependencies & Installation Instructions 

### Quickstart <a name = "quick-start"></a> 

Install all devDependencies in one line 
```
npm eslint eslint-config-airbnb eslint-config-node eslint-config-prettier eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-node eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks prettier --save-dev
```


### <img src="https://d33wubrfki0l68.cloudfront.net/204482ca413433c80cd14fe369e2181dd97a2a40/092e2/assets/img/logo.svg" width="45" height="20">  ESLint <a name = "eslint"></a> 


ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

#### Installation
##### Local Install
```
npm install eslint --save-dev
```
##### Global Install (Not Recommended)
- It is also possible to install ESLint globally rather than locally (using npm install eslint --global). However, this is not recommended, and any plugins or shareable configs that you use must be installed locally in either case.
```
npm install eslint --global
```
#### See Docs
- [Getting Started Guide: ESLint](https://eslint.org/docs/user-guide/getting-started)

---

### <img src="https://news.airbnb.com/wp-content/themes/presser/resources/assets/favicon/favicon.ico" width="20" height="20">  Airbnb Styles Guide & ESLint <a name = "airbnb"></a>

#### Airbnb Styles Guide ESLint NPM
[NPM Package Link: eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb)

#### Airbnb-ESLint Installation For React

Run For _React Projects_
```
npm info "eslint-config-airbnb@latest" peerDependencies
```

OR Shortcut For _React Projects_
```
npx install-peerdeps --dev eslint-config-airbnb
```
##### Troubleshooting Tip
If npm errors out and you receive a message like `ERR undefined` in your terminal try :
```
npm install eslint-config-airbnb@18.2.1 eslint@^7.2.0 eslint-plugin-import@^2.22.1 eslint-plugin-jsx-a11y@^6.4.1 eslint-plugin-react@^7.21.5 eslint-plugin-react-hooks@^1.7.0 --save-dev
```

#### Run Eslint Init (create .eslintrc.json)
This will walk you through a config setup. Skip if you wish and just go to create a `.eslintrc.json` file yourself. 

If you make a mistake in the setup it doesn't matter. You can change anything in the `.eslintrc.json` file whenever you wish.
```
npx eslint --init
```
##### _OR to create an empty config file_
```
echo {}> .eslintrc.json
```

#### Example ESlint & Airbnb & Prettier
Add to the .eslintrc.json config file for example:
- Note if you don't want to use Prettier mentions of it in this file  
```
{
  "extends": ["airbnb", "airbnb/hooks", "prettier"],
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": [
      "error",
      {
        "endOfLine": "auto"
      }
    ],
    "no-unused-vars": "warn",
    "no-console": "warn",
    "func-names": "off",
    "no-process-exit": "off",
    "object-shorthand": "off",
    "class-methods-use-this": "off",
    "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
  },
  "settings": {
    "import/resolver": {
      "node": {
        "moduleDirectory": ["node_modules", "src/"]
      }
    }
  }
}
```

#### See the Docs

- [ESLint Rules](https://eslint.org/docs/rules/)
  
- [ESLint Config](https://eslint.org/docs/user-guide/configuring/)

- [ESLint User Guide](https://eslint.org/docs/2.13.1/user-guide/configuring)

- Note For Usage *Without React* Use [eslint-config-airbnb-base](https://www.npmjs.com/package/eslint-config-airbnb-base)

---

### <img src="https://prettier.io/icon.png" width="20" height="20"> Prettier <a name = "prettier"></a>

#### Prettier VS CODE
Get the Prettier Extension & Install for VS Code
- [Prettier Extension in VS Code](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)


#### Installation
Install Prettier locally

```
npm install --save-dev --save-exact prettier
```
Create an empty config file with Git
```
touch .prettierrc
```
#### Example Prettier

Add to .prettierrc your configuration settings for example:
```
{
  "singleQuote": false
}
```

#### See the docs
- [Prettier Configuration Docs](https://prettier.io/docs/en/configuration.html)

---

### Absolute Paths React <a name ="abs-paths"></a>

#### What Are Absolute Paths?
Instead of...
```
import Icon from './../../components/icon';
```
Absolute paths allow imports like so:
```
import Icon from components/icon';
```

To use absolute paths in React
- Create jsconfig.json file with Git
```
touch jsconfig.json
```
- & add something like...

##### Example

```
{
  "compilerOptions": {
    "baseUrl": "src",
    "module": "commonjs",
    "target": "es2016",
    "jsx": "react"
  },
  "exclude": ["node_modules", "**/node_modules/*"],
  "include": ["src"]
}
```
In the above example we assume that the `src` folder is the directory where all the code lives for the React project.

Therefore `src` will be your base path for the imports. Otherwise you can modify the configuration above to fit your project's needs.

##### Another Simple Example:
```
{
  "compilerOptions": {
    "baseUrl": "src"
  },
  "include": ["src"]
}
```

##### Note About JavaScript projects (jsconfig.json)
`"exclude": ["node_modules", "**/node_modules/*"],` or the `include` line allows refers to including or excluding node modules from these from type checking & and Intellisense stuff in VS Code. See more details about setuping up a jsconfig in the VS Code docs: [Working with JavaScript](https://code.visualstudio.com/docs/nodejs/working-with-javascript#_writing-jsconfigjson)


---

## <img src="https://avatars.githubusercontent.com/u/366329?s=200&v=4" width="20" height="20"> Additional Configurations Examples & Tutorials <a name = "tutorials"></a>
#### Paulo Ramos Examples
- [Paulo Ramos Github: eslint-prettier-airbnb-react](https://github.com/paulolramos/eslint-prettier-airbnb-react)

#### Colt Steele Tutorial
- [Improve Your Code With ESLint + VsCode + Airbnb Styleguide](https://www.youtube.com/watch?v=mfGkKlMDfwQ&t=565s)


#### Wes Bos Tutorial
- [ESLint + Prettier + VS Code — The Perfect Setup
](https://www.youtube.com/watch?v=lHAeK8t94as)

#### Traversy Media Tutorial
- [VSCode ESLint, Prettier & Airbnb Style Guide Setup
](https://www.youtube.com/watch?v=SydnKbGc7W8)
- [Github Setup Tutorial](https://gist.github.com/bradtraversy/aab26d1e8983d9f8d79be1a9ca894ab4)


