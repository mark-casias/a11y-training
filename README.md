#
## Package Features
### Asset packagist support
The Asset packagist package acts as a bridge between Composer and the popular NPM and Bower repositories, which catalog 
thousands of useful front-end and JavaScript packages. This allows developers to easily pull in packages like DropZoneJS
and many others without requiring local Node.js to be installed. 

Read more: https://lightning.acquia.com/blog/round-your-front-end-javascript-libraries-composer

### Guardr core security
Guardr is a Drupal distribution with a combination of modules and settings to enhance a Drupal application's security 
and availability to meet enterprise security requirements. This project leverages Guardr's package management.

### Sub-profile support
A Drupal core patch has been included to add support for "Sub-profiles".

See: https://www.drupal.org/node/1356276 

### Support for installs from existing configuration
A Drupal core patch has been included to allow projects to be installed from existing configuration.

See: https://www.drupal.org/node/2788777

## Setting up a local [Vagrant](http://vagrantup.com) environment

### Clone this repository into the directory of your choice:
- `$ git clone git@bitbucket.org:mediacurrent/mis_rain_vagrant.git`

### Edit your local `/etc/hosts` file to include the new box IP
    192.168.50.110 mcrain.mcdev

### Install composer on host machine
- On MacOS ```brew install composer```
- Otherwise, see instructions here https://getcomposer.org/

### Run the build script.
- `$ ./scripts/build.sh`

This script automates the following steps:

* Runs composer install
* Ensures vagrant is available
* Starts vagrant if required
* Installs the project Drupal site

The initial pass of the build script downloads several dependencies and an intermittent internet connection will affect the initial build process.

### Troubleshooting
* Ensure Vagrant has provisioned without errors. Correct errors before proceeding. After vagrant provision is successful it maybe be helpful to vagrant halt && vagrant up`

## Drush Alias
* Use the project's [drush alias file](drush/mcrain.mcdev.aliases.drushrc.php)
* Optionally copy into your user's drush directory at ~/.drush/ for global use or customization.

## Logging In
* Use `drush @mcrain.mcdev uli` to login to your local installation.

## Development Settings
* The ./web/sites/mcrain.mcdev/settings.local.php contains settings for customizing the development environment.  This disables Drupal's built in caching and additionally activates sites/development.services.yml for further customizing the development environment.

# Development Workflow

* [Use Composer](https://bitbucket.org/mediacurrent/drupal-project/src/HEAD/README.md) to add 3rd party dependencies and patches.
* Write custom modules, themes etc. to the ./web/ directory.
* Run `drush @mcrain.mcdev cex` to export Drupal configuration to the profile/profilename/config/sync folder.
* Run `$ ./scripts/build.sh` before starting a new ticket. Run build.sh again to test work completed prior to submitting a pull request.

## Demo Content
* TBD

## Additional Links
* [Project Drupal Theme Guide](https://bitbucket.org/mediacurrent/mis_rain_vagrant.git/src/HEAD/web/themes/custom/project_theme/README.md?fileviewer=file-view-default)
* [Using Vagrant](https://bitbucket.org/mediacurrent/mis_vagrant/src/HEAD/README.md)
