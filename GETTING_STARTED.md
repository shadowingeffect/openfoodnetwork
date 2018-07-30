### Getting Started

This is a general guide to setting up an Open Food Network development environment on your local machine.

The following guides are located in the wiki and provide more OS-specific step-by-step instructions:

- [Ubuntu Setup Guide][ubuntu]
- [macOS Sierra Setup Guide][sierra]
- [OSX El Capitan Setup Guide][el-capitan]

### Dependencies

* Rails 3.2.x
* Ruby 2.1.5
* PostgreSQL database
* PhantomJS (for testing)
* See Gemfile for a list of gems required

If you are likely to need to manage multiple version of ruby on your local machine, we recommend version managers such as [rbenv](https://github.com/rbenv/rbenv) or [RVM](https://rvm.io/).

For those new to Rails, the following tutorial will help get you up to speed with configuring a [Rails environment](http://guides.rubyonrails.org/getting_started.html).

### Get it

If you're planning on contributing code to the project (which we [LOVE](CONTRIBUTING.md)), it is a good idea to begin by forking this repo using the `Fork` button in the top-right corner of this screen. You should then be able to use `git clone` to copy your fork onto your local machine.

    git clone https://github.com/YOUR_GITHUB_USERNAME_HERE/openfoodnetwork

Jump into your new local copy of the Open Food Network:

    cd openfoodnetwork

And then add an `upstream` remote that points to the main repo:

    git remote add upstream https://github.com/openfoodfoundation/openfoodnetwork

Fetch the latest version of `master` from `upstream` (ie. the main repo):

    git fetch upstream master

### Get it running

First, you need to create the database user the app will use by manually typing the following in your terminal:

```sh
$ sudo -u postgres psql -c "CREATE USER ofn WITH SUPERUSER CREATEDB PASSWORD 'f00d'"
```

This will create the "ofn" user as superuser and allowing it to create databases.

Once done, run `script/setup`. If the script succeeds you're ready to start developing. If not, take a look at the output as it should be informative enough to help you troubleshoot.

If you run into any other issues getting your local environment up and running please consult [the wiki](wiki).

If still you get stuck do not hesitate to open an issue reporting the full output of the script.

Now, your dreams of spinning up a development server can be realised:

    bundle exec rails server

To login as Spree default user, use:

    email: spree@example.com
    password: spree123

### Testing

Tests, both unit and integration, are based on RSpec. To run the test suite, first prepare the test database:

    bundle exec rake db:test:prepare

Then the tests can be run with:

    bundle exec rspec spec

The project is configured to use [Zeus](zeus) to reduce the pre-test startup time while Rails loads. See the [Zeus GitHub page](zeus) for usage instructions.

Once [npm dependencies are installed](karma), AngularJS tests can be run with:

    ./script/karma run

If you want karma to automatically rerun the tests on file modification, use:

    ./script/karma start

### Multilingual
Do not forget to run `rake tmp:cache:clear` after locales are updated to reload I18n js translations.

### Rubocop
The project is configured to use [rubocop](rubocop) to automatically check for style and syntax errors.

You can run rubocop against your changes using:

    rubocop


[developer-wiki]: https://github.com/openfoodfoundation/openfoodnetwork/wiki
[sierra]: https://github.com/openfoodfoundation/openfoodnetwork/wiki/Development-Environment-Setup:-macOS-(Sierra)
[el-capitan]: https://github.com/openfoodfoundation/openfoodnetwork/wiki/Development-Environment-Setup:-OS-X-(El-Capitan)
[ubuntu]: https://github.com/openfoodfoundation/openfoodnetwork/wiki/Development-Environment-Setup:-Ubuntu
[wiki]: https://github.com/openfoodfoundation/openfoodnetwork/wiki
[zeus]: https://github.com/burke/zeus
[rubocop]: https://rubocop.readthedocs.io/en/latest/
[karma]: https://github.com/openfoodfoundation/openfoodnetwork/wiki/Karma
