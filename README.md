# adminer-table-filter
Adminer plugin for quickly filtering tables, works only with custom themes where table list holds floated items

Uses localStorage to hold the filter across url changes

![Screenshot](/../screenshots/table-filter.png "Table filter using custom theme")

## Fresh Installation

1. Download [plugin.php](https://raw.github.com/vrana/adminer/master/plugins/plugin.php) to `/plugins` directory 
2. Copy `quiclfilter.php` to `/plugins` director
3. Adminer should be renamed to `adminer.php`
4. Create `index.php` and paste this
```
<?php
function adminer_object() {
    // required to run any plugin
    include_once "./plugins/plugin.php";
    
    // autoloader
    foreach (glob("plugins/*.php") as $filename) {
        include_once "./$filename";
    }
    
    $plugins = array(
        // specify enabled plugins here
        new AdminerQuickFilterTables,
    );
    
    /* It is possible to combine customization and plugins:
    class AdminerCustomization extends AdminerPlugin {
    }
    return new AdminerCustomization($plugins);
    */
    
    return new AdminerPlugin($plugins);
}

// include original Adminer or Adminer Editor
include "./adminer.php";
?>
```
5. Add `new AdminerQuickFilterTables` to `index.php` `$plugins` array
6. Download [Theme](https://raw.githubusercontent.com/vrana/adminer/master/designs/pepa-linha/adminer.css) to `adminer.css`

## Dependencies

* `localStorage` capable browser
* Adminer theme, where the table list items are floated elements
