# Convert meta.yml to Backstage catalog-info.yml

An action that takes your repository's meta.yml and outputs + commits a Backstage compatible catalog-info.yml

Usage should be within a workflow that triggers on an update to the meta.yml

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
    - name: Generate Backstage catalog config from meta.yml
      id: makecatalog
      uses: ndustrialio/ndustrial-actions/meta-to-backstage-catalog@master
```