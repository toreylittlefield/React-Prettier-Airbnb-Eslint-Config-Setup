# Visual Studio Code - ESLint, Prettier, JSConfig & Airbnb Setup For JS / React Projects
---

## This document outlines a setup for React projects in VS Code. 

### Implements the following: 
- Linting rules using [Airbnb style guide](https://airbnb.io/javascript/react/) & [ESLint](https://eslint.org/)
- Formatting code with the [Prettier Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- Using absolute paths/imports with [jsconfig.json](https://code.visualstudio.com/docs/languages/jsconfig)


---
## 📝 Table of Contents

- [ESLint](#eslint)
- [Airbnb Styles](#airbnb)
- [Prettier](#prettier)
- [Tutorials & Resources](#tutorials)

---

## Dependencies & Installation Instructions 


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
Run Eslint Init
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

### <img src="https://prettier.io/icon.png" width="20" height="20"> Prettier Installation & Config <a name = "prettier"></a>

#### Prettier VS CODE
Get the Prettier Extension & Install for VS Code
- [Prettier Extension in VS Code](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)


#### Installation
Install Prettier locally

```
npm install --save-dev --save-exact prettier
```
Create an empty config file
```
echo {}> .prettierrc.json
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
## <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 576 512" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg"><path d="M528.3 46.5H388.5c-48.1 0-89.9 33.3-100.4 80.3-10.6-47-52.3-80.3-100.4-80.3H48c-26.5 0-48 21.5-48 48v245.8c0 26.5 21.5 48 48 48h89.7c102.2 0 132.7 24.4 147.3 75 .7 2.8 5.2 2.8 6 0 14.7-50.6 45.2-75 147.3-75H528c26.5 0 48-21.5 48-48V94.6c0-26.4-21.3-47.9-47.7-48.1zM242 311.9c0 1.9-1.5 3.5-3.5 3.5H78.2c-1.9 0-3.5-1.5-3.5-3.5V289c0-1.9 1.5-3.5 3.5-3.5h160.4c1.9 0 3.5 1.5 3.5 3.5v22.9zm0-60.9c0 1.9-1.5 3.5-3.5 3.5H78.2c-1.9 0-3.5-1.5-3.5-3.5v-22.9c0-1.9 1.5-3.5 3.5-3.5h160.4c1.9 0 3.5 1.5 3.5 3.5V251zm0-60.9c0 1.9-1.5 3.5-3.5 3.5H78.2c-1.9 0-3.5-1.5-3.5-3.5v-22.9c0-1.9 1.5-3.5 3.5-3.5h160.4c1.9 0 3.5 1.5 3.5 3.5v22.9zm259.3 121.7c0 1.9-1.5 3.5-3.5 3.5H337.5c-1.9 0-3.5-1.5-3.5-3.5v-22.9c0-1.9 1.5-3.5 3.5-3.5h160.4c1.9 0 3.5 1.5 3.5 3.5v22.9zm0-60.9c0 1.9-1.5 3.5-3.5 3.5H337.5c-1.9 0-3.5-1.5-3.5-3.5V228c0-1.9 1.5-3.5 3.5-3.5h160.4c1.9 0 3.5 1.5 3.5 3.5v22.9zm0-60.9c0 1.9-1.5 3.5-3.5 3.5H337.5c-1.9 0-3.5-1.5-3.5-3.5v-22.8c0-1.9 1.5-3.5 3.5-3.5h160.4c1.9 0 3.5 1.5 3.5 3.5V190z"></path></svg> Additional Configurations Examples & Tutorials <a name = "tutorials"></a>
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


