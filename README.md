# Starter Plugin

This is a [YOOtheme Pro](https://yootheme.com) plugin for Joomla/WordPress. It is a minimal example plugin that can be used as a starting point for your own plugin development.

## Requirements

The following software needs to be installed and running on your system.

| Name     | Description                                                                |
|----------|----------------------------------------------------------------------------|
| Composer | PHP Dependency Manager [https://getcomposer.org/](https://getcomposer.org/) |
| NodeJS   | JavaScript Runtime [https://nodejs.org/](https://nodejs.org/) |
| Task     | To run build tasks you need to install [Task](https://taskfile.dev) via Node and npm or use another [installation method](https://taskfile.dev/installation/) of your choice.|

## Getting Started

After you have installed PHP and Composer, you create a new plugin project via Composer's create-project command. This will create a new `my-plugin` directory with the plugin files.
It's recommended to create the plugin folder inside the CMS plugin folder (Joomla `plugins/system` / WordPress `wp-content/plugins`)

```bash
composer create-project yootheme/starter-plugin my-plugin
```

You will be asked for additional plugin information, this will be used when building the plugin.

- `Enter plugin title:` The Plugin title
- `Enter plugin description:` Description
- `Enter author name:` Author Name
- `Enter author email:` Author Email
- `Enter author url:` Author URL


Once the plugin has been created you will find a new folder `build` in the plugin directory.
In here you find a `joomla` and `wordpress` folder containing the plugin blueprint files.

These files contain placeholders for the information provided earlier. The placeholder are replaced by the `build` and `setup` tasks when the plugin is built.

| System    | files                            |
|-----------|----------------------------------|
| Joomla    | my-plugin.php <br> my-plugin.xml |
| WordPress | my-plugin.php |

## Create Module

Create a new module run the command:

`composer create:module <name>`

### Arguments

| arg  | Description     |
|------|-----------------|
| name | The module name |

### Questions

- `Enter module namespace:` Enter optional PHP namespace
- `Add module assets example? [Y/n]` Include an example how to load custom assets in the module? (default Yes)
- `Add settings example? [Y/n]` Include an example how create settings for the module? (default Yes)

## Create Element

Create new elements with the command:

`composer create:element <name> (<module>)`

### Arguments

| arg    | Description     |
|--------|-----------------|
| name   | The element name |
| module | The module name to which this element will be added. If you have multiple modules and do not provide the module, a list of your modules will be suggested. <br>  The command errors if no module have been created before. |

### Questions

- `Create multiple items element? [y/N]` Create an element that contains multiple items (like a Grid element) (default No)
- `Enter element title:` The element title


## Tasks

### Setup

The setup tasks copy the plugin files from the `build` folder to the root and replaces the placeholders so it can be discoverd and installed in Joomal/WordPress.

If you are developing the plugin in Joomla use `task setup-joomla` or `task setup-wordpress` when you develop in a WordPress environment.

### Build

Creates an installable zip archive of the plugin.

Run the task `task build` to create a zip archive for Joomla and WordPress. Or you can create the archives individually by running `task build-joomla` or `task build-wordpress`

## License

[MIT](https://opensource.org/licenses/MIT)
