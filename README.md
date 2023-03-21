# heroku-buildpack-ssh-multikey

Add ssh keys to your build.

Adapted from [heroku/heroku-buildpack-ssh-key](https://github.com/heroku/heroku-buildpack-ssh-key).

## Usage

1. Add the buildpack to your Heroku app:

   ```
   $ heroku buildpacks:add https://github.com/sciencecorp/heroku-buildpack-ssh-multikey -i 1
   ```

   Keep in mind that the buildpack order is important. If you'll specify this buildpack after your default one (e.g. `heroku/nodejs`) it'll not work. See [https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app) for details.

2. Set `BUILDPACK_SSH_KEYS` to the private SSH keys you want added, concatenated together:

   ```
   $ heroku config:set BUILDPACK_SSH_KEYS="$(cat keys.txt)"
   ```

The buildpack will save the SSH keys to your build at `~/.ssh/keyN`.
