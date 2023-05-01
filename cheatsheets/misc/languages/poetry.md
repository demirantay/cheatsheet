# Poetry

## Project Creation

#### Creating a new project
```sh
poetry new project_name
```

#### Initialising a pre-existing projec
```sh
cd pre-existing-project
poetry init
```

#### The .toml file that is created
```toml
[tool.poetry]
name = "poetry-demo"
version = "0.1.0"
description = ""
authors = ["Sébastien Eustace <sebastien@eustace.io>"]

[tool.poetry.dependencies]
python = "*"

[tool.poetry.dev-dependencies]
pytest = "^3.4"
```

## Library Installment

#### Add a new lib
```sh
potry add <library>
```

#### Remove a lib
```sh
poetry remove <library>
```

#### Update a lib
```sh
poetry update <library>
```

#### Display the package information
```sh
poetry show
```

## Dependencies

#### Installing dependencies
```sh
poetry install
```

#### Lock the project dependencies
```sh
poetry lock
```

#### Update the dependencies according to the pyproject.toml file
```sh
poetry update
```

## Virtual Env

#### Activate the Python virtual environment
```sh
cd ./project-name
poetry shell
```

#### Deactivate the Python virtual environment
```sh
exit
```

#### Get venv path
```sh
poetry run which python
```

#### List the existing Python virtual environments associated with a Poetry project:
```sh
cd rocketship
poetry env list
```

#### Delete the Python environment
```sh
# poetry env remove <python-environment-name>
# Ex:
poetry env remove rocketship-DKQKySEf-py3.8
```

## Misc

1 - Edit `pyproject.toml`:
```toml
[tool.poetry.scripts]
test = 'scripts:test'
```
2 - Create a `scripts.py` file on the root directory of your project:
```python
import subprocess

def test():
    """
    Run all unittests. Equivalent to:
    `poetry run python -u -m unittest discover`
    """
    subprocess.run(
        ['python', '-u', '-m', 'unittest', 'discover']
    )
```
3 - Run script:
```sh
poetry run test
```