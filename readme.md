
# docker-wp-deploy

Capistrano powered WordPress deployment, adapted for a local docker environment.

Based on wp-deploy (https://github.com/Mixd/wp-deploy)

## Docker-specific features

This variant requires a similar setup to wp-deploy - it is still a Capistrano base, and requires a similar Ruby installation. The docker environment replaces the requirement to have a local PHP/MySQL installation, and WP-CLI is handled from within docker.

### Docker-specific commands

Note: most wp-deploy commands work as normal (e.g. wp:setup:local will still need to be run to set up the local WordPress environment)

-**Start Environment**: 'docker-compose up' - this will bring up the required frontend and database containers. By default this repo currently uses nginx, php 7.3 and mysql 5.7, these can be adjusted in the docker-compose.yml.
-**wp-cli**: normal wp-cli commands now need to run through a docker container. the wp-cli container in the base docker-compose file is referred to as 'cli', so a docker-aware wp-cli command would now be reformatted from 'wp ...' to 'docker-compose run --rm cli ...'. This will spin up a temporary wp-cli container to run your command.

---

This repository utilises the Capistrano 3 framework to help the deployment and successful launch of a WordPress based website.

## Features

That sounds fancy, but what does it actually do?

- **Install WordPress**: WordPress is created at a git submodule* and installed based on your pre-defined configuration.
- **Environment based git deployment**: Clone an entire repository (from anywhere) to the server. Have separate environments to deploy to? (think: production/staging) We've got you covered.
- **Deployment rollbacks**: Realised you deployed a version thats going to break the site? Run a command to revert your changes to the previous version.
- **Push/Pull database with correct URLs**: Override the environment's database and run a 'search and replace' through the database to make sure the URLs are correct for that environment.
- **Push/Pull uploads**: Update you entire uploads directory from local to <environment> or vice versa.
- **Update WordPress**: Update your version of WordPress with ease, straight from the Command Line.
- **Configuration templates**: Need specific attributes within your `.htaccess` or `wp-config.php`? The templates are designed for this in mind and allow you to do this on an environment by environment basis.
- **Setup permissions**: Make sure your uploads and `.htaccess` files are readable from the get-go.

## Requirements

- **Git > v1.7.3**: Git is used to pull down the website from your Git hosting and therefore is a mandatory requirement.
- **SSH access**: For wp-deploy (or Capistrano in general) to work you need SSH access both between your local machine and your remote server, and between your local machine and your Git hosting (Github, Bitbucket, CodebaseHQ, etc) account.
- **Bundler**: As WP-Deploy comes with various different Ruby Dependencies, Bundler is used to make quick work of the installation process. Here's the [link](http://bundler.io/)
- **WP-CLI (greater than 0.22.0)**: WP-Deploy also requires the automation of WordPress functions directly in the Command Line. As these functions are required on all environments (local, staging and production servers), we make use of the WordPress Command Line Interface. You can check out the [documentation](http://wp-cli.org/#install) on how to get this setup.

In addition, as this is powered by WordPress, you'll also need to follow [WordPress' requirements](https://codex.wordpress.org/Hosting_WordPress).

## Unsupported/Untested tech

Some of the following tech is more untested than anything else. This could be due to time constraints or unfamiliarity with the software:

- Nginx
- Git (lower than version 1.7.3)
- WP-CLI (lower than version 0.22.0)
- Capistrano 3.8 or lower.
- Another shell besides Bash/Zsh for local development
- WordPress Multisite

Want to support these? Create a fork of the project, let us know and once vetted we'll happily provide a link in here to your project.

## Installation

Take a look at the [Installation Guide](https://github.com/Mixd/wp-deploy/wiki/Installation).

## Usage

Take a look at the [Usage Guide](https://github.com/Mixd/wp-deploy/wiki/Usage).

## FAQ

Take a look at the [Frequently Asked Questions](https://github.com/Mixd/wp-deploy/wiki/FAQ).

## Contributing

Take a look at the [Contributing guide](https://github.com/Mixd/wp-deploy/wiki/Contributing)

## Credits

This project is developed by the [Mixd](http://www.mixd.co.uk) team. Like it? Hate it? Let us know on [Twitter](http://twitter.com/mixd).
