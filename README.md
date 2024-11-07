<p align="center">
    <img src="https://github.com/user-attachments/assets/5fabe4cb-8fdc-4132-8281-56f87774b414" width="240" height="110">
</p>

# Starter Plugin

The YOOtheme Starter Plugin is a ready-to-use starter kit to help you build your next [YOOtheme Pro](https://yootheme.com) extension. Easily create a module for YOOtheme Pro to extend its functionalities. For example, add setting panels to the customizer, elements to the page builder or load needed asset files into the site. It takes care of all the tedious tasks, like the integration into Joomla or WordPress, and helps with distribution, versioning and updating of your YOOtheme Pro extension, so you can focus on the actual features.

## Requirements

Install [Composer v2.5+](https://getcomposer.org/download/), which is used to install PHP packages.

Also, use Node and npm to install [Task](https://taskfile.dev/), which is needed to run build tasks.

```bash
npm install -g @go-task/cli
```

## Create a new plugin

To create a new plugin, run Composer's `create-project` command in the plugins folder of WordPress `wp-content/plugins` or Joomla `plugins/system`. Replace `PLUGIN_NAME` with the name of your plugin, for example `myplugin`.

```bash
composer create-project yootheme/starter-plugin PLUGIN_NAME
```

After Composer has installed the YOOtheme Starter Plugin package, you need to run the `create:plugin` command.

```bash
composer create:plugin
```

You will be asked for additional plugin information which will be used in the plugin metadata.

- **Enter plugin title:** The plugin title, for example `My Plugin`
- **Enter plugin description:** The plugin description
- **Enter author name:** The author Name
- **Enter author email:** The author email
- **Enter author url:** The author URL, for example `https://example.com`
- **Enter update server url:** The URL to the update server file, for example `https://example.com/updates`

This will create a new `myplugin` directory with required plugin files.

```
.
├── build                  # Plugin blueprint files
│   ├── joomla
│       ├── myplugin.php   # Joomla plugin
|       ├── myplugin.xml   # Joomla plugin metadata
│   ├── wordpress
│       ├── myplugin.php   # WordPress plugin
|   └── Taskfile.yml       # build tasks
├── .env                   # Metadata
├── vendor                 # Development dependencies
├── README.md
└── Taskfile.yml           # Main Taskfile
```

## Set up the plugin

To make your new plugin available in WordPress or Joomla, run the corresponding setup task in the plugin root folder. This will copy the necessary plugin files from the `build` folder to the plugin root folder.

```bash
task setup-wordpress
task setup-joomla
```

Now the plugin can be discovered and installed in WordPress or Joomla.

## Create a new module

To create a new YOOtheme Pro module, which is a package of code that extends the functionality of YOOtheme Pro, run the following command and replace `MODULE_NAME` with the name of your module, for example `my-module`.

```bash
composer create:module MODULE_NAME
```

You will be asked further questions to configure the module.

- **Enter module namespace:** Enter a PHP namespace, for example `MyPlugin\MyModule`
- **Add asset files example? [y/N]** Press Enter for _No_.
- **Add settings example? [y/N]** Press Enter for _No_.
- **Add custom LESS example? [y/N]** Press Enter for _No_.
- **Add custom source example? [y/N]** Press Enter for _No_.
- **Add translation files example? [y/N]** Press Enter for _No_.

Read the [Modules documentation](https://yootheme.com/support/yootheme-pro/joomla/developers-modules) to learn more about the created files and code examples.

**Note:** Add `wordpress` or `joomla` to the name for system-specific modules, for example `my-module-wordpress` or `my-module-joomla`. The build tasks will only copy the relevant modules into the WordPress and Joomla zip archives.

## Create a new element

To create a new element, run the following command and replace `ELEMENT_NAME` with the name of your element, for example `my-element`. If there are multiple modules, choose a module from the provided list.

```bash
composer create:element ELEMENT_NAME
```

Optionally, define the module where the element should be created.

```bash
composer create:element ELEMENT_NAME MODULE_NAME
```

You will be asked further questions to configure the element.

- **Enter element title:** The element title, for example `My Element`
- **Enter element group:** Press Enter for `Custom`.
- **Create multiple items element? [y/N]** Press Enter for _No_.
- **Include Element transform example? [y/N]** Press Enter for _No_.

Read the [Elements documentation](https://yootheme.com/support/yootheme-pro/joomla/developers-elements) to learn more about the created files and code examples.

## Build distribution files

To create an installable zip archive of the plugin for WordPress and Joomla, run the following `build` task. The created zip files are located in the `dist` folder.

```bash
task build
```

Alternatively, create the archives individually.

```bash
task build-wordpress
task build-joomla
```

## Publishing and versioning

To raise the version number of your plugin or change metadata, like the plugin title or description, edit the `.env` file in the root folder.

```yaml
TITLE='My Plugin'
NAME='myplugin'
VERSION='0.0.1'
DESCRIPTION='Lorem ipsum'
DATE='{{ now | date "2006-01-02" }}'
COPYRIGHT='Copyright (C)'
LICENSE='GNU General Public License'
AUTHOR='My Company'
AUTHOREMAIL='me@example.com'
AUTHORURL='https://example.com'
```

After changing the metadata, re-run the corresponding Joomla or WordPress [setup task](#user-content-set-up-the-plugin) to update the plugin files and run the [build task](#user-content-build-distribution-files) to create new distribution files.

## Update Server

To enable 1-click updates in WordPress and Joomla, run the [build task](#user-content-build-distribution-files) to generate the necessary update server files for WordPress `dist/update.json` and Joomla `dist/update.xml`. These files are configured based on the package information in the `.env` file.

```yaml
# Update server
UPDATEURI='https://example.com/updates'

# Package information
STABILITY='stable'
DOWNLOADURL='https://example.com/downloads'
PHPMINIMUM='7.4'
JOOMLAMINIMUM='(5\.[01]|4\.[01234]|3\.10)\.'
WORDPRESSMINIMUM='6.2'
```

Upload these files to the `UPDATEURI` URL. This URL is where your plugin checks for updates and retrieves the associated download file. Ensure the zip archives from the `dist` folder are uploaded to the location specified in `DOWNLOADURL`.

## Updating commands and tasks

The command and task scripts have their own [starter-utils](https://github.com/yootheme/starter-utils) Github repository. To update the package to the latest version, run `composer update` from time to time.

## Github

To make your plugin a Git repository use `git init -b main` and follow the steps under [Adding a local repository to GitHub using Git](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git).

## License

[MIT](https://opensource.org/licenses/MIT)
