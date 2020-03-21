# Creating a new Node Project
The steps to creating a new node project in my current Ubuntu dev environment.

## 1. Create the directory
```
mkdir new-project-name
cd new-project-name
```

## 2. Initialise the project
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

## 3. Adding Jest as a dependency
```
npm install --save-dev jest@23.6.0
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
## 4. Add a basic test
Create "Greeting" test and functionality:

From the project root:
```
mkdir tests
```

Create test file:
```
// ./tests/greeting.test.js
  const greeting = require('../greeting');

  describe('greeting()', () => {
    it('says hello', () => {
      expect(greeting('Nemo')).toBe('Hello, Nemo!');
    });
  });      
```

Create functionality:
```
// ./greeting.js
  module.exports = (name) => {
    return `Hello, ${name}!`
  };      
```

Run the test:
```
npm test
```

## 5. Setup git
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

## 6. Configure Jest in watch mode.
From VS Code terminal in project root:
```
npx jest --watchAll
```

Modify the test file and Jest should auto update when it is saved:
```
// ./tests/greeting.test.js
  const greeting = require('../greeting');
      ...
      expect(greeting('Nemo')).toBe('Hello, Nemo!');
      expect(greeting('Waldo')).toBe('Hello, Waldo!');
      ...  
```

## 7. Install and Configure ESLint with Jest support
First quit Jest if it's still running *Q* then
from VS Code terminal in project root:
```
npm install --save-dev eslint@5.10.0
npm install --save-dev eslint-plugin-jest@22.1.2
```

Create ESLint configuration file in the project root:
```
// .eslintrc.js
module.exports = {
  extends: ['eslint:recommended'],
  parserOptions: {
    ecmaVersion: 6,
  },
  env: {
    node: true,
  },
};
```

Create ESLint configuration file in the test directory:
```
// ./tests/eslintrc.js
module.exports = {
  plugins: ['jest'],
  extends: ['plugin:jest/recommended'],
};
```

Check all is well; no feed back from either:
```
npx eslint greeting.js
npx eslint ./tests/greeting.test.js
```

Install ESLint plugin for linting as you code, open extensions
sidebar (ctrl+shift+x), search for "ESLint" install Dirk Baeumer's version.

Your code will now be linted as you type, this can be changed to as you save, search for other config options.

## 8. Install, configure and integrate Prettier with VS Code
Run from project root:
```
npm install --save-dev prettier-eslint-cli@4.7.1
npm install --save-dev eslint-config-prettier eslint-plugin-prettier
```

Install Prettier plugin for linting as you code, open extensions
sidebar (ctrl+shift+x), search for "ESLint" install Dirk Baeumer's version.

Edit ESLint configuration file in the project root:
```
// .eslintrc.js
module.exports = {
  extends: ['eslint:recommended', 'plugin:prettier/recommended'],
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
