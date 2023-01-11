# json-loader
Github action that reads and outputs the contents of a Json file. This Github action has the following inputs and outputs parameters:

## Inputs

* json-file: Json file that has to be read.

## Outputs

* json-contents: Contents of the Json file that can be used as argument to [fromJSON](https://docs.github.com/en/actions/learn-github-actions/expressions#fromjson) Github expression.

# Usage example 

```yaml
on: [push]

jobs:
  Json_file_read_job:
    runs-on: ubuntu-latest
    name: A job to read a json file
    steps:
      - uses: actions/checkout@v3
      - id: read-json
        uses: ajuanicorena/json-loader@v1
        with:
          json-file: 'config.json'
      - run: echo "One value fromJSON ${{ fromJSON(steps.read-json.outputs.json-contents).<key to read> }}"
```