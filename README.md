# Starter Plugin

This is a [YOOtheme Pro](https://yootheme.com) plugin for Joomla/WordPress. It is a minimal example plugin that can be used as a starting point for your own plugin development.

## Getting Started

After you have installed PHP and Composer, you create a new plugin project via Composer's create-project command. This will create a new `my-plugin` directory with the plugin files.

```bash
composer create-project yootheme/starter-plugin my-plugin
```

To run build tasks you need to install [Task](https://taskfile.dev) via Node and npm or use another [installation method](https://taskfile.dev/installation/) of your choice.

```bash
npm install -g @go-task/cli
```

## Create new Plugin

To create a new Joomla and WordPress plugin run the command:

`composer create:plugin <name>`

### Arguments

*name*
    The plugin name

### Questions

You will be asked for additional plugin information

`Enter plugin title:` - The Plugin title
`Enter plugin description:` - Description
`Enter author name:` - Author Name
`Enter author email:` - Author Email
`Enter author url:` - Author URL


## Create Module

To create a new module in the plugin run the command:

`composer create:module <name>`

### Arguments

*name*
    The module name

### Questions

`Enter module namespace:` - Enter optional PHP namespace
`Add module assets example? [Y/n]` - Include an example how to load custom assets in the module? (default Yes)
`Add settings example? [Y/n]` - Include an example how create settings for the module? (default Yes)

## Create Element

You can create new elements with the command:

`composer create:element <name> (<module>)`

### Arguments

*name*
    The element name

*module*
    The module name to which this element will be added. If you have multiple modules and do not provide the module, a list of your modules will be suggested.
    The command errors if no module have been created before.

### Questions

`Create multiple items element? [y/N]` - Create an element that contains multiple items (e.g. Grid element) (default No)
`Enter element title:` - The element title


## License

[MIT](https://opensource.org/licenses/MIT)
