# Starter Plugin

The YOOtheme starter kit provides a minimal and simple starting point for building your next [YOOtheme Pro](https://yootheme.com) extension. Easily create a module for YOOtheme Pro to extend its functionalities. For example, add setting panels to the customizer, elements to the page builder or load needed asset files into the site. Once the module is customized based on your application's needs, automatically build a Joomla plugin and WordPress plugin to distribute it to your customer project.

## Technical Requirements

Install [Composer](https://getcomposer.org/download/), which is used to install PHP packages.

Also, use Node and npm to install [Task](https://taskfile.dev/), which is needed to run build tasks.

```bash
npm install -g @go-task/cli
```

## Create a new plugin

To create a new plugin run the following command in the plugins folder of WordPress `wp-content/plugins` or Joomla `plugins/system` depending on your preferred development environment. Replace `PLUGIN_NAME` with the name of your plugin, for example `my-plugin`.

```bash
composer create-project yootheme/starter-plugin PLUGIN_NAME
```

You will be asked for additional plugin information which will be used in the plugin metadata.

- **Enter plugin title:** The plugin title, for example `My Plugin`
- **Enter plugin description:** The plugin description
- **Enter author name:** The author Name
- **Enter author email:** The author email
- **Enter author url:** The author URL

This will create a new `my-plugin` directory with required plugin files.

```
.
├── build                   # Plugin blueprint files
│   ├── joomla
│       ├── my-plugin.php   # Joomla plugin
|       ├── my-plugin.xml   # Joomla plugin metadata
│   ├── wordpress
│       ├── my-plugin.php   # WordPress plugin
├── vendor                  # Development dependencies
├── LICENSE.md
└── README.md
```

## Set up the plugin

Open your new plugin folder in the terminal and use one of the following task to copy the necessary plugin files from the `build` folder to the plugin root folder.

```bash
task setup-wordpress
task setup-joomla
```

Now the plugin can be discoverd and installed in WordPress or Joomla.

## Create a new module

To create a new module run the following command and replace `MODULE_NAME` with the name of your module, for example `my-module`.

```bash
composer create:module MODULE_NAME
```

You will be asked further questions to configure the module.

- **Enter module namespace:** Enter a PHP namespace, for example `MyPlugin/MyModule`
- **Add asset files example? [y/N]** Enter defaults to *No*.
- **Add settings example? [y/N]** Enter defaults to *No*.

Read the [Modules documentation](https://yootheme.com/support/yootheme-pro/joomla/developers-modules) to learn more about the created files and code examples.

## Create a new element

To create a new element run the following command and replace `ELEMENT_NAME` with the name of your element, for example `my-element`. If there are multiple modules, choose a module of the provided list.

```bash
composer create:element ELEMENT_NAME
```

Optionally define the module where the element should be created.

```bash
composer create:element ELEMENT_NAME MODULE_NAME
```

You will be asked further questions to configure the element.

- **Enter element title:** The element title, for example `My Element`
- **Create multiple items element? [y/N]** Enter defaults to *No*.

Read the [Elements documentation](https://yootheme.com/support/yootheme-pro/joomla/developers-modules) to learn more about the created files and code examples.

## Build distribution files

To create an installable zip archive of the plugin for WordPress and Joomla, run the following task. The created zip files are located in the `dist` folder.

```bash
task build
```

Alternatively, create the archives individually.

```bash
task build-wordpress
task build-joomla
```

## Publishing and versioning 

To raise the version number of your plugin or change metadata like the plugin title or description, open the `Taskfile.yml` and edit the options under `vars:`.

After that, re-run the [setup task](#user-content-set-up-the-plugin) to update the plugin for your develop environment meaning WordPress or Joomla and run the [build task](#user-content-build-distribution-files) to create the distribution files.

In order keep the starter kit files as minimal as possible all utilities are separated in their own [starter-utils](https://github.com/yootheme/starter-utils) Github repository. To update to the latest version from time to time, run `composer update`.

## Github

To make your plugin a Git repository use `git init -b main` and follow the steps under [Adding a local repository to GitHub using Git](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git).

## License

[MIT](https://opensource.org/licenses/MIT)
