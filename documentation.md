# YAML

- **YAML** Ain't Markup Language™  
- **YAML** is a human-friendly data serialization
  language for all programming languages.  
- You can specify key: pair values as `key: pair`.  
e.g. Below json equivalanet of YAML

```json
{
    "firstname": "John",
    "lastname": "Smith"
}
```

```yaml
firstname: John
lastname: Smith
```

- Nested objects written as below, the child properties are written with spaced indentation same as python.

```yml
address:
    city: Pune
    country: India
    pincode: 444444
```

- `Comments` are written with line start with `#...`

```yaml
#This is comment
```

- **Arrays** or list of items/objets written as below.
- `-` (hypen/dash) denoted the start of new item/object.

```yml
mylist:
    - itemId: itemId1
      itemName: itemOne
    - itemId: itemId2
      itemName: itemTwo
```

- It is important to have your YML file has valid syntax. To check syntax validation we can use some online linter e.g. [codebeautify yaml validator](https://codebeautify.org/yaml-validator)

- `Multi line strings` are written as follows.
The `|` operator is used to denote the multi line string.

```yml
long_string: |
    This is multiline string.
    It includes more than two sentences.
    You can denote is by using | (pipe) symbol,
    immediately after specifying the key. (A space needed bafore | ).
```

## Configuration of first action

- Name: The name of the workflow as it will appear in the Actions tab of the GitHub repository.
- on: Specifies the trigger for this workflow. on is an event handler which triggers the action on specified event/s. Most common used events are `push`, `pull_request`.
- jobs: Groups together all the jobs that run in the github-actions workflow.
- runs-on: ubuntu-latest - Configures the job to run on the latest version of an Ubuntu Linux runner.
- steps: Groups together all the steps that run in the job. Each item nested under this section is a separate action or shell script.

```yml
name: My First Github Action
on: [push]
jobs:
  print-hello-world:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Hello world..."
      - run: echo "Second hello world..."
```

## Adding actions/checkout@v2

- This action checks-out your repository under `$GITHUB_WORKSPACE`, so your workflow can access it.
- Only a single commit is fetched by default, for the ref/SHA that triggered the workflow.

```yml
name: My First Github Action
on: [push]
jobs:
  build-app:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: echo "Hello world..."
```

## Setup node js action

```yml
...
build-app:
  runs-on: ubuntu-latest
  steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-node@v2
      with:
        node-version: '14.17.0'
    - run: node -v
```

### Writing build action

- Install the packages
- Build the project

```yml
- name: Install packages
  run: npm i
- name: Build a project
  run: npm run build
- name: Setup finish
  run: echo 'Build created.'
```