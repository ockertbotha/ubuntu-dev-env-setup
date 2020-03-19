## 1. Installing Node and npm using NVM
Sourced from:
- https://linuxize.com/post/how-to-install-node-js-on-ubuntu-18.04/
- https://github.com/nvm-sh/nvm#installing-and-updating


```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

This should copy NVM repository to `~/.nvm` directory and add the following to your terminal profile
(`~/.bash_profile`,`~/.zshrc`,`~/.profile`,`~/.bashrc`)
```
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

Verify nvm was installed properly:
```
nvm --version
```

## 2. Installing Node.js and npm
Install the latest LTS version:
```
nvm install --lts
```

List installed Node.js versions:
```
nvm ls
```

Node and npm should be installed:
```
node -v
```
```
npm -v
```
