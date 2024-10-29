# SETTINGS

Loads settings from (csv) files.

## Usage

Add the `SETTINGS.tox` to your project (doesn't matter where) and make sure its `opshortcut` parameter has a value (default value: `SETTINGS`).

By default it loads the defaults from `./settings.defaults.csv` and the project settings from `./settings.csv`. The settings file can be overwritten through an env var (by default: `settings`).

## API

Get a reference to the CHOP containing all the numeric settings (can also be used in a `select` CHOP):

```
op.SETTINGS.Chop
```

Get a refer4ence to the DAT operator containing all the settings values (can also be used in a `select` DAT):

```
op.SETTINGS.Dat
```

Programmatically get a single setting value:

```
op.SETTINGS.Get('<setting_name>')
```

(Programmatically) set a single setting value (auto-saves settings file):

```
op.SETTINGS.Set('<setting_name>', '<value>')
```

Set value without auto-saving:

```
op.SETTINGS.Set('<setting_name>', '<value>', save=False)
```

Programmatically Save/Load settings:

```
op.SETTINGS.Save()
op.SETTINGS.Load()
```
