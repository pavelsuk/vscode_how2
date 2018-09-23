# Visual Studio Code - settings and hints

## General

### Extensions

#### Git

- [GitLens - Git supercharged](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
    - You will have to provide personal token for this extensions - see [docs on Marketplace](https://marketplace.visualstudio.com/items?itemName=KnisterPeter.vscode-github)
- [Start git-bash](https://marketplace.visualstudio.com/items?itemName=McCarter.start-git-bash#review-details)

### Markdown

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [Markdown Preview Github Styling](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-preview-github-styles)
- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
    - You can change settings for the markdownlint either in [.markdownlint.json in your project](.markdownlint.json) or in your user or [workspace setting](.vscode/settings.json).

**Example:** [.markdownlint.json:](.markdownlint.json)

``` json
{       "default": true,
        "MD007": { "indent": 4 },
        "MD013": false,
        "MD024":{"siblings_only":true},
        "no-hard-tabs": false
}
```

**Example:** [workspace setting](.vscode/settings.json)

``` json
    "markdownlint.config": {
        "default": true,
        "MD007": { "indent": 4 },
        "MD013": false,
        "MD024":{"siblings_only":true},
        "no-hard-tabs": false
    }
```

### Other

- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

## Python Development

### Installed modules (via conda)

- [Google Formatter for Python Files](https://github.com/google/yapf) `conda install -c conda-forge yapf`
- [Flake8](http://flake8.pycqa.org/en/latest/) `conda install -c conda-forge flake8`
- pytest `conda install -c conda-forge pytest`
  
All modules in one script:  

``` bash
conda install -c conda-forge yapf
conda install -c conda-forge flake8
conda install -c conda-forge pytest
```

Optionally `conda install -c conda-forge jedi`

### Extensions

- [Anaconda Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-python.anaconda-extension-pack) installs
    - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
    - [YAML Support by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)  
- [autoDocstring](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring)
- [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)

### Settings

#### Selecting Conda Environment

- Press `Ctrl+Shift+P` and start typing `Python int` to get to  `Python: Select Interpreter`
- Choose the conda environment you want to use in your project
- You can see changes directly in your [Workspace settings](.vscode/settings.json)

``` json
    "python.pythonPath": "C:\\dev\\Anaconda3\\envs\\py36\\python.exe"
```

- If it doesn't work correctly (eg. your terminal is not switching to specific environment), you can play with settings for your terminal and add

``` json
    "terminal.integrated.shellArgs.windows": [
        "/K",
        "C:/dev/Anaconda3/Scripts/activate.bat",
        "C:/dev/Anaconda3/envs/py36"
    ]
```

#### Formating

- You can configure the format provider by changing a setting in the User or Workspace settings file as follows:

``` json
"python.formatting.provider": "yapf"
```

- You can fine tune yapf settings by adding [.style.yapf](.style.yapf) to the root directory of your project. My typical change is

``` ini
# The column limit.
column_limit=120
```

- See also
      - [Formatting  Python in Visual Studio Code](https://donjayamanne.github.io/pythonVSCodeDocs/docs/formatting)
      - [Google Formatter for Python Files](https://github.com/google/yapf)

#### Linting

- You can configure default linter either by pressing `Ctrl+Shift+P` and start typing `lint` to get to `Python: Select Linter` or by changing it in [Workspace settings](.vscode/settings.json)

``` json
    "python.linting.pylintEnabled": false,
    "python.linting.flake8Enabled": true,
    "python.linting.enabled": true,
```
