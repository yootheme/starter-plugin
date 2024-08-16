# Starter Plugin

This is a [YOOtheme Pro](https://yootheme.com) plugin for Joomla/WordPress. It is a minimal example plugin that can be used as a starting point for your own plugin development.

## Requirements

The following software needs to be installed and running on your system.

| Name     | Description                                                                |
|----------|----------------------------------------------------------------------------|
| Composer | PHP Dependency Manager [https://getcomposer.org/](https://getcomposer.org/) |
| Task     | To run build tasks you need to install [Task](https://taskfile.dev) via Node and npm or use another [installation method](https://taskfile.dev/installation/) of your choice.|

## Getting Started

After you have installed PHP and Composer, you create a new plugin project via Composer's create-project command. This will create a new `my-plugin` directory with the plugin files.

It's recommended to create the plugin folder inside the CMS plugin folder (Joomla `plugins/system` | WordPress `wp-content/plugins`)

```bash
composer create-project yootheme/starter-plugin my-plugin
```

You will be asked for additional plugin information, this will be used in the plugin metadata.

- `Enter plugin title:` The Plugin title
- `Enter plugin description:` Description
- `Enter author name:` Author Name
- `Enter author email:` Author Email
- `Enter author url:` Author URL


### Folder Structure

Once the plugin has been created you will find the following folder structure in the plugin.

```
.
├── build                   # Plugin blueprint files
│   ├── joomla
│       ├── my-plugin.php   # Joomla plugin
|       ├── my-plugin.xml   # Joomla plguin metadata
│   ├── wordpress
│       ├── my-plugin.php   # WordPress plugin
├── vendor                  # development dependencies
├── LICENSE.md
└── README.md
```

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

### Folder Structure

Please check the [Developer Documentation](https://yootheme.com/support/yootheme-pro/joomla/developers-modules) for a detailed explanation of a modules functionality.

```
modules                              # Modules are added to this folder
├── my-module
|   ├── assets                        # Asset examples (Depends on choice in create command)
|      ├── js
|      ├── css
|   ├── config                        # Config examples (Depends on choice in create command)
|      ├── customizer.json
|   ├── src                           # Depending on the choices in the create command
|      ├── AssetsListener.php
|      ├── SettingssListener.php
|   ├── bootstrap.php                 # Module definition
```

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

### Folder Structure

Please check the [Developer Documentation](https://yootheme.com/support/yootheme-pro/joomla/developers-elements) for detailed explanation of Builder Elements.

```
my-module                       # Elements are added to the specified module
├── elements
    ├── my-element              # Element definition and templates
        ├── templates
        ├── element.json
    ├── my-element_item         # Multiple items element definition and templates
        ├── templates
        ├── element.json
        ├── element.php
```


## Tasks

### Setup

The setup tasks copy the plugin files from the `build` folder to the root and replaces the placeholders so it can be discoverd and installed in Joomal/WordPress.

If you are developing the plugin in Joomla use `task setup-joomla` or `task setup-wordpress` when you develop in a WordPress environment.

### Build

Creates an installable zip archive of the plugin.

Run the task `task build` to create a zip archive for Joomla and WordPress. Or you can create the archives individually by running `task build-joomla` or `task build-wordpress`

## License

[MIT](https://opensource.org/licenses/MIT)
