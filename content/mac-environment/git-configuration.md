# Configuración de Git en Mac

## Instalar git

Podemos instalar Git a través de brew con el siguiente comando:

`brew install git`

**Referencia:** [Installing Git](https://git-scm.com/book/en/v1/Getting-Started-Installing-Git#Installing-on-Mac)

## Añadir colores e información de la rama actual

Podemos habilitar los colores y añadir información sobre la rama actual añadiendo el siguiente código en el `~/.bash_profile`.

```bash
# I like tunning the colors of the prompt in the first place:
export CLICOLOR='true'
export  LSCOLORS="gxfxcxdxbxCgCdabagacad"
export EDITOR=vi
 
# Git branch in good-looking prompt.
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
 
# Prompt with Git branch
# Explanation of the weird lines: \u Username, \h Host, \w Path, tput setaf is the color definition
 
export PS1='\[$(tput setaf 7)\]\u@\[$(tput setaf 2)\]\h:\[$(tput setaf 4)\]\w\[$(tput setaf 1)\]$(parse_git_branch)\[$(tput sgr0)\] $ '
```

**Referencia:** [Terminal tuning for Git developers in Mac](http://www.harecoded.com/terminal-tuning-for-git-developers-in-mac-2364711)

## Instalar bash-completion

Ahora hay que instalar bash-completion para que nos ayude con el **autocompletado de las ramas y otros comandos de Git**.

### Instalar bash completion desde brew

`brew install bash-completion`

Ahora tenemos que añadir el siguiente código en el `~/.bash_profile`:

```bash
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

**Referencia:** [Install Bash git completion](https://github.com/bobthecow/git-flow-completion/wiki/Install-Bash-git-completion)

## Instalar Git Credential Manager

Git Credential Manager está disponible para Mac y Linux. En la [documentación](https://github.com/Microsoft/Git-Credential-Manager-for-Mac-and-Linux) podemos ver cómo [instalarlo en Mac](https://github.com/Microsoft/Git-Credential-Manager-for-Mac-and-Linux/blob/master/Install.md#how-to-install).

### Actualizar Brew

` brew update `

### Instalar Git Credential Manager

`brew install git-credential-manager`


`git-credential-manager install`


### Deshabilitar las credenciales alternativas (opcional)

`git config --global credential.canFallBackToInsecureStore false `