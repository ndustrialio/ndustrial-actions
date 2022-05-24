# Convert meta.yml to Backstage catalog-info.yml

An action that takes your repository's meta.yml as input and outputs the contents of a Backstage compatible catalog-info.yml

Usage should be within a workflow that triggers on an update to the meta.yml and commits the output to a catalog-info.yml file.

## Usage

```yaml
name: Generate Backstage catalog-info

on:
  push:
    branches: [main]
    paths: 
      - 'meta.yaml'
  pull_request:
    branches: [main]
    paths: 
      - 'meta.yaml'
jobs:
  create-backstage-config:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Generate Backstage catalog config from meta.yml
      id: makecatalog
      uses: ndustrialio/ndustrial-actions/meta-to-backstage-catalog@master
      with:
        meta: cat ~/meta.yml
    - name: Create new catalog-info.yml
      run: echo ${{ steps.makecatalog.outputs.catalog-info }} > ~/catalog-info.yml

    - name: Check for changes
      run: git status
    - name: Stage changes
      run: git add .
    - name: Config github 
      run: |
        git config --global user.name 'Backstage Automation'
        git config --global user.email 'devops@ndustrial.io'
    - name: Commit changes
      run: git commit -m "Auto update"
    - name: Push to master
      run: git push
```