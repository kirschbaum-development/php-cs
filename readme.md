# Preflight
1. Clone `kirschbaum-development/php-cs`
2. `cd kirschbaum-development/php-cs`
3. `composer install`

# IDE Configuration
## PHPStorm
#### Inspections (fixer does not run, only highlights violations)
1. Set the correct php cs fixer binary in:
    - Language & Frameworks -> PHP -> Quality tools
2. Place the KDG custom .php_cs configuration file in your home directory
3. Within phpstorm, go to:
    - Settings -> Editor -> Inspections -> PHP -> Quality tools
    - Make sure PHP CS Fixer validation is checked
    - In the right hand pane, after selecting this option, click the browse (`...`) button and select the .php_cs file previously saved in your home directory
    - Ensure PHP Code Sniffer validation is also set to this Coding Standard in its right pane
    - Click Apply and OK

> **IntelliJ idea** users
> 
> Be sure to upgrade to >= 2021.1
> Install `File watchers` plugin
> use .php_cs from kirschbaum-development/php-cs/.php_cs not home directory

#### File Watcher (fixer runs on save action)
1. In PHPStorm, create a file watcher (under "Preferences->Tools")
2. Uncheck all of the "Advanced Options"
3. Edit the following settings:
```
Name: PHP Style fixer
File type: PHP
Scope: Current File
Path: /{your-global-composer-directory}/vendor/friendsofphp/php-cs-fixer/php-cs-fixer
Arguments: fix $FileDir$/$FileName$ --verbose --config={path-to-your-root-php-cs-dir}/php-cs/.php_cs
```
## VS Code
1. Install [PHP CS Fixer](https://marketplace.visualstudio.com/items?itemName=fterrag.vscode-php-cs-fixer) extension
2. Configure Extension, in `Settings as JSON`
    ```
    "vscode-php-cs-fixer.config": "/{path_to_repository}/.php_cs",
    "vscode-php-cs-fixer.toolPath": "/{path_to_repository}/vendor/bin/php-cs-fixer",
    "[php]": {
        "editor.defaultFormatter": "fterrag.vscode-php-cs-fixer"
    },
    ```
## Sublime Text 3
1. Find `PHP CS Fixer` using Package Control: Install Package (cmd-shift-p)
2. Under Preferences -> Package Settings -> PHP CS Fixer -> Settings - User, configure the extension using the following JSON
    ```
    {
        "config": "/path/to/kirschbaum-development/php-cs/.php_cs",
        "on_save": true,
    }
    ```
