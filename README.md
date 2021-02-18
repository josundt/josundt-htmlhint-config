# @josundt/htmlhint-config #

> Ruleset for HTML code style and linting

## Usage ##
1. Install this package 

2. Add npm task in **package.json**
    ```json
    {
      "scripts": {
        "lint:html": "htmlhint src -c ./node_modules/@josundt/htmlhint-config/.htmlhintrc --format unix"
      }
    }
    ```

3. When using Visual Studio Code:  

    __a)__ Install the htmllint extension (_"mkaufman.htmlhint"_), and add it
       to the recommmended extensions for the workspace (_".vscode/extensions.json"_).

    __b)__ Add a task in _".vscode/tasks.json"_ to run sass-lint as a VSCode task for the
       whole workspace:
    ```json
    {
      "version": "2.0.0",
      "runner": "terminal",
      "tasks": [
        {
          "label": "lint:html",
          "type": "shell",
          "command": "npx",
          "args": [
            "htmlhint",
            "src",
            "-c",
            "./node_modules/@josundt/htmlhint-config/.htmlhintrc",
            "--format",
            "unix"
          ],
          "group": "build",
          "presentation": {
            "echo": true,
            "reveal": "silent",
            "focus": false,
            "panel": "shared"
          },
          "problemMatcher": {
            "applyTo": "allDocuments",
            "severity": "error",
            "fileLocation": "absolute",
            "source": "lint:sass",
            "pattern": [
              {
                "regexp": "(.*):(\\d+):(\\d+): (.*)",
                "file": 1,
                "line": 2,
                "column": 3,
                "message": 4
              }
            ]
          }
        }
      ]
    }
    ```
