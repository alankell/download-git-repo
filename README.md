# git-download-cli

Download and extract a git repository (GitHub, GitLab, Bitbucket) from node.

## Installation

    $ npm install git-download-cli

## API

### download(repository, destination, options, callback)

Download a git `repository` to a `destination` folder with `options`, and `callback`.

#### repository
The short hand repository string to download the repository from:

- GitHub - `github:owner/name` or simply `owner/name`
- GitLab - `gitlab:owner/name`
- Bitbucket - `bitbucket:owner/name`

The `repository` parameter defaults to the `master` branch, but you can specify a branch or tag as a URL fragment like `owner/name#my-branch`.
In addition to specifying the type of where to download, you can also specify a custom host like `gitlab:custom.com:owner/name`.
Feel free to submit an issue or pull request for additional host options.

#### destination
The file path to download the repository to.

#### options
An optional options object parameter with download options. Options include:

- `clone` - boolean default `false` - If true use `git clone` instead of an http download. While this can be a bit slower, it does allow private repositories to be used if the appropriate SSH keys are setup.

#### callback
The callback function as `function(err)`.

## Examples
Using http download from Github repository at master.
```javascript
download('flipxfx/download-git-repo-fixture', 'test/tmp', function(err) {
  if (err) return done(err);
  done();
});
```

Using git clone from Bitbucket repository at my-branch.
```javascript
download('bitbucket:flipxfx/download-git-repo-fixture#my-branch', 'test/tmp', { clone: true }, function(err) {
  if (err) return done(err);
  done();
});
```

## Thanks

To [flipxfx/download-git-repo](https://github.com/flipxfx/download-git-repo) for the head start.

## License

MIT

