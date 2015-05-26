# [Surge](https://surge.sh) git hooks example

An example of using git hooks with npm run scripts and Surge.

## Getting started

To try out this example, clone the project and add a test commit and you’ll be prompted to publish.

In your own project, install [Surge](https://github.com/sintaxi/surge) and [git-scripts](https://github.com/nkzawa/git-scripts):

```sh
npm install --save-dev surge git-scripts
```

Next, in your `package.json`, add the git hook you’d like to run your npm task on. Finally, add add a `npm run` task for Surge:

```json
"git": {
  "scripts": {
    "post-commit": "npm run deploy",
    "pre-push": "npm run deploy"
  }
},
"scripts": {
  "deploy": "surge --project ./ --domain my-project.surge.sh"
}
```

Now, anyone can `npm run deploy` to use Surge, and they will also deploy `post-commit` and `pre-push` (note the later requires git 1.8.x and up).

In practice, you probably won’t want to publish `post-commit`, but `pre-push` is very useful. The full list of hooks is [available here](https://github.com/nkzawa/git-scripts#description).

## License

[The MIT License (MIT)](LICENSE.md)

Copyright © 2015 [Chloi Inc.](http://chloi.io)
