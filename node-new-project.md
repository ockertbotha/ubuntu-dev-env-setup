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

.git and ignore, vs code setup.
