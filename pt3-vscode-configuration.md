# Configure VS Code
The steps to getting VS Code setup:

## 1. User settings
From the Command Palette (ctrl+shift+p):
```
Preferences: Open Settings (JSON)
```

Add:
```
{
  ...
  "workbench.settings.useSplitJSON": true,
  "editor.codeActionsOnSave": {
      "source.fixAll.eslint": true,
      "source.fixAll.tslint": true,
      "source.fixAll.stylelint": true
  },  
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  ...
}
```

Save and reopen.

## 2. Workspace settings
With user settings open, select *WORKSPACE* option, found next to
*USER* title of settings page. This adds new file to a project
root *.vscode/settings.json* where we add the following:
```
// .vscode/settings.json
{
  "files.exclude": {
    "node_modules": true,
    "package-lock.json": true,
  },
  "[javascript]": {
    "editor.tabSize": 2
  }
}
```
