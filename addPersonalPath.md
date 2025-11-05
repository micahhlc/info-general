

cat $HOME/.zprofile


# example
` export PATH="/Users/micahcheng/anaconda3/bin:$PATH"`
` eval "$(/opt/homebrew/bin/brew shellenv)"`


# Add personal shell path to $PATH

## Option 1
```
export PATH="$HOME/Git/info-shell-script:$PATH"
```

To apply changes immediately (without reboot):
`source ~/.zprofile`

## Option 2
add to .zshrc
Add Git/info-shell-script

`export PATH="$HOME/Git/info-shell-script:$PATH"`

To update your path env
```
vim ~/.zprofile
source ~/.zprofile
```