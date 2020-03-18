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
npm init
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
// package.json
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
