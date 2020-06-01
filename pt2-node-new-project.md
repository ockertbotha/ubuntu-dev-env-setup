# Creating a new Node Project
The steps to creating a new node project in my current Ubuntu dev environment.

## 1. Create the directory
```
mkdir new-project-name
cd new-project-name
```

## 2. Setup git
From the project root:
```
git init
```

Create git ignore:
```
// ./gitignore
node_modules/
.vscode/
```

## 3. Initialise the project
Accept the default responses when initialising:
```
npm init -y
```

Set the npm registry to private:
```
// package.json
...
  "name": "new-project-name",
  "private": true,
  "version": "1.0.0",
...
```

## 4. Adding Babel
```
npm install --save-dev @babel/core@7.2.0
npm install --save-dev @babel/preset-react@7.0.0 @babel/preset-env@7.2.0
```

Make accessible:
```
// ./.babelrc.js
module.exports = {
  presets: ['@babel/preset-react', '@babel/preset-env'],
};
```

## 5. Adding Jest and Babel as dependencies
```
npm install --save-dev jest@23.6.0 babel-jest@23.6.0
npm install --save-dev babel-core@^7.0.0-bridge.0
```

Check it was installed with:
```
npx jest --version
```

Set Jest as default test script:
```
// ./package.json
...
  "scripts": {
    "test": "jest"
  },
...
```

Check it worked with
```
npm test
```

## 6. Add a basic test
Create "Greeting" test and functionality:

From the project root:
```
mkdir tests
```

Create test file:
```
// ./src/tests/greeting.test.js
  const greeting = require('../greeting');

  describe('greeting()', () => {
    it('says hello', () => {
      expect(greeting('Nemo')).toBe('Hello, Nemo!');
    });
  });      
```

Create functionality:
```
// ./src/greeting.js
  module.exports = (name) => {
    return `Hello, ${name}!`
  };      
```

Run the test:
```
npm test
```

## 7. Install React and add test
```
npm install react@16.4.2 prop-types@15.7.2
npm install --save-dev react-dom@16.4.2
```

Create test file:
```
// ./src/tests/greeting-react.test.js
  import React from 'react';

  describe('JSX', () => {
    it('calls React.createElement', () => {
        const createElementSpy = jest.spyOn(React, 'createElement');
        <h1>Hello, JSX!</h1>;
        expect(createElementSpy).toHaveBeenCalledWith('h1', null, 'Hello, JSX!');
      });    
  });      
```

Check it worked:
```
npx jest
```

## 7. Install and Configure ESLint
Note: pt3-vscode-configuration-node must also be completed for all of this to work.

From VS Code terminal in project root:
```
npm install --save-dev eslint@5.10.0 eslint-plugin-jest@22.1.2 eslint-plugin-react@7.11.1 babel-eslint@10.0.1
npm install --save-dev --save-dev @babel/plugin-proposal-class-properties@7.1.0
```

Update Babel config:
```
// ./.babelrc.js
module.exports = {
  ...
  plugins: ['@babel/plugin-proposal-class-properties'],
  ...
};
```

Create ESLint configuration file in the project root:
```
// .eslintrc.js
module.exports = {
  extends: ['eslint:recommended', 'plugin:react/recommended'],
  parser: 'babel-eslint',
  parserOptions: {
    ecmaVersion: 6,
    sourceType: 'module',
    ecmaFeatures: {
      jsx: true,
    },
  },
  env: {
    node: true,
  },
  settings: {
    react: {
      version: '16.4.2',
    }
  }
};
```

Create ESLint configuration file in the test directory:
```
// ./src/tests/.eslintrc.js
module.exports = {
  plugins: ['jest'],
  extends: ['plugin:jest/recommended'],
};
```

Add ESLint configuration file to src folder:
```
// ./src/.eslintrc.js
module.exports = {
  env: {
    browser: true,npm install --save-dev --save-dev @babel/plugin-proposal-class-properties@7.1.0
  },
};
```

Check all is well; no feed back from:
```
npx eslint ./src/greeting.js
npx eslint ./src/tests/greeting.test.js
npx eslint ./src/tests/greeting-react.test.js
```

Install ESLint plugin for linting as you code, open extensions
sidebar (ctrl+shift+x), search for "ESLint" install Dirk Baeumer's version.

Your code will now be linted as you type, this can be changed to as you save, search for other config options.

## 8. Install, configure and integrate Prettier with VS Code
Run from project root:
```
npm install --save-dev prettier-eslint-cli@4.7.1 eslint-config-prettier eslint-plugin-prettier
```

Install Prettier plugin for linting as you code, open extensions
sidebar (ctrl+shift+x), search for "Prettier - Code formatter" install Esben Petersen's version.

Edit ESLint configuration file in the project root:
```
// .eslintrc.js
module.exports = {
  extends: [... ,'plugin:prettier/recommended'],
  ...
};
```

Create Prettier configuration file in the project root:
```
// .prettierrc.js
module.exports = {
  trailingComma: 'es5',
  tabWidth: 2,
  semi: true,
  singleQuote: true,
};
```

Set Lint and Prettier as default scripts:
```
// ./package.json
...
  "scripts": {
    "test": "jest"
    "lint": "eslint . && prettier-eslint --list-different **/*.js",
    "format": "prettier-eslint --write **/*.js"    
  },
...
```
The check it all works:
```
npm run format
```

## 9. Use Wallaby
Create Wallaby configuration file in the project root:
```
// wallaby.js
module.exports = function(wallaby) {
  return {
    testFramework: 'jest',
    env: {
      type: 'node',
    },
    tests: ['src/tests/**/*.test.js'],
    files: ['src/**/*.js', '!**/*.test.js', '!**/.*'],

    compilers: {
      '**/*.js': wallaby.compilers.babel(),
    },
  };
};
```
Open command palette (ctrl+shift+p) and run Wallaby.js: Start command.

## 10. Using Enzyme
Note: consider switching to react-testing-library (https://github.com/kentcdodds/react-testing-library)

From VS Code terminal in project root:
```
npm install --save-dev enzyme@3.8.0 enzyme-adapter-react-16@1.7.1
```

Note: Add the Jest setup for enzyme here
Create Wallaby configuration file in the project root:
```
// wallaby.js
module.exports = function(wallaby) {
  return {
    testFramework: 'jest',
    env: {
      type: 'node',
    },
    tests: ['src/tests/**/*.test.js'],
    files: ['src/**/*.js', '!**/*.test.js', '!**/.*'],

    compilers: {
      '**/*.js': wallaby.compilers.babel(),
    },
  };
};
```
