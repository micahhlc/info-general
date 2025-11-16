# about NVM
## see version of node.js
`nvm ls `

## install latest node
 `nvm install --lts      `

## use the latest version
`nvm use node`

## set as default version to use
`nvm alias default node`

## see config of nvm
`nvm alias`


```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```