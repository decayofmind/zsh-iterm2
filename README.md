# zsh-iterm2-utilities

Simple, but smart ZSH plugin, helping to download various iTerm2 utilities.
The plugin allows to omit clonning of the whole iterm2-website repository or
relying to other repos, where those utilities may be out of sync.

This project utilizes GitHub actions to poll the original iterm2-website repo daily,
then it takes sha256 checksum of all scripts in utilities directory and commits
to this repository.

So, if utilities in iterm2-website master are updated, this repo gets updated to.

Zplugin allows to execute a special command at pull and clone (see snippet below),
the plugin is using that opportunity to download all the utilities.

At ZSH init, only `path` will be extended.

## Zinit (former Zplugin)

```
zinit ice as"command" pick"bin/*" atclone'./_utils/download_files.sh' \
  atpull'%atclone' if"[[ $+ITERM_PROFILE ]]"
zinit light decayofmind/zsh-iterm2-utilities

# functions
zinit snippet 'https://raw.githubusercontent.com/gnachman/iterm2-website/master/source/shell_integration/zsh'
```
