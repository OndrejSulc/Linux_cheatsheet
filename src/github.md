### Subrepositories in github action

1) create PAT token under user that as access to all those subrepositories
- User > settings > Developer settings > Personal access tokens > Fine-grained tokens
- select repositories to grant access
- add code + metadata access
- add contents access
- save generated token

2) add token to repository with github action
- go to Settings > Secrets and variables > Actions
- add new repository secret
- paste generated token

3) use token in github action during code pull
```
name: unit-tests

on:
  pull_request:
    branches: [main]

jobs:
  unit-tests:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3
        with:
          submodules: 'recursive'
          token: ${{ secrets.PAT_TOKEN }}
          
      - name: Setup node
        uses: actions/setup-node@v3
        with:
          node-version: 18.16
    
      - name: Install npm dependencies
        run: npm install

      - name: Run unit tests
        run: npm test
``` 
