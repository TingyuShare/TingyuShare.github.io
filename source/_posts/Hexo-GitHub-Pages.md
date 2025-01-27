---
title: MarkDown 博客小试
date: 2022-04-11
tags: hexo
---
快速组织一下我设置 Hexo blog 用到的资源, 好了记录一个美好的开始吧！
##  Quick Start Hexo
```shell
$ npm install hexo-cli -g
$ hexo init blog
$ cd blog
$ npm install
```
##  Local Hexo Blog
```shell 
$ hexo new "My New Post"
$ hexo clean && hexo g && hexo s
```

## GitHub Pages
In this tutorial, we use [GitHub Actions](https://docs.github.com/en/actions) to deploy GitHub Pages. It works in both public and private repository. Skip to the [One-command deployment](#One-command-deployment) section if you prefer not to upload your source folder to GitHub.

1. Create a repo named <b>*username*.github.io</b>, where username is your username on GitHub. If you have already uploaded to other repo, rename the repo instead.
2. Push the files of your Hexo folder to the default branch of your repository. The default branch is usually **main**, older repository may use **master** branch.
  - To push `main` branch to GitHub:

    ```
    $ git push -u origin main
    ```
  - The `public/` folder is not (and should not be) uploaded by default, make sure the `.gitignore` file contains `public/` line. The folder structure should be roughly similar to [this repo](https://github.com/hexojs/hexo-starter), without the `.gitmodules` file.

3. Check what version of Node.js you are using on your local machine with `node --version`. Make a note of the major version (e.g., `v16.y.z`)
4. Create `.github/workflows/pages.yml` in your repo with the following contents (substituting `16` to the major version of Node.js that you noted in previous step):

```yml .github/workflows/pages.yml
name: Pages

on:
  push:
    branches:
      - main  # default branch

jobs:
  pages:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js 16.x
        uses: actions/setup-node@v2
        with:
          node-version: '16'
      - name: Cache NPM dependencies
        uses: actions/cache@v2
        with:
          path: node_modules
          key: ${{ runner.OS }}-npm-cache
          restore-keys: |
            ${{ runner.OS }}-npm-cache
      - name: Install Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

5. Once the deployment is finished, the generated pages can be found in the `gh-pages` branch of your repository.
6. In your GitHub repo's setting, navigate to **Settings** > **Pages** > **Source**. Change the branch to `gh-pages` and save.
7. Check the webpage at *username*.github.io.

Note - if you specify a custom domain name with a `CNAME`, you need to add the `CNAME` file to the `source/` folder. [More info](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

## Useful links

- [GitHub Pages](https://docs.github.com/en/pages)
- [peaceiris/actions-gh-pages](https://github.com/marketplace/actions/github-pages-action)
