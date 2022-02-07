## Knowledge Required:

 - React Components;
 - Props;
 - Proptypes.

## Preview:

![image](preview.gif)

## Deploy

**File:** `github/workflows/build.yml`

**Add on package.json:** `"homepage": "Movie-Library/",`

```
name: deploy

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: '14.x'
      - name: Build web-app
        run: |
          npm ci
          npm run build
      - name: Deploy to gh-pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```


