AngularJS
================
This module is supposed to be the new version of the AngularJS 
project(https://www.drupal.org/project/angularjs) for Drupal 8.

### Installation
1. Copy the module folder to [drupal_installation_rootfolder]/modules directory.
2. Enable the module at /admin/modules.
3. You can use it in your modules as a standard core library through render arrays.

### Basic example
First of all, you have to add 'angularjs' as a dependency for your module in info.yml.

Then include the needed library into your build array, for example:

```
class MyController extends ControllerBase {
  public function myPage() {
    $build = array();
    $build['#attached']['library'][] = 'angularjs/angular';
    
    //random code
    
    return $build;
  }
}
```

But this is not a common thing to use it alone, usually we create our own 
javascript which use the angularjs library. This can be done via mymodule.libraries.yml.
Define your library in this way:

```
mymodule-scripts:
  version: VERSION
  js:
    js/myscript.js: {}
  css:
    component:
      css/mystyle.css: {}
  dependencies:
    - angularjs/angular
```

You also have to register your library in mymodule.info.yml:

```
name: 'This is a module'
type: module
...
libraries:
 - mymodule/mymodule-scripts
```

Now you can use it in render arrays like this:
```
$build['#attached']['library'][] = 'mymodule/mymodule-scripts';
```

### Available angular modules
The angular framework has a lot of modules, now these are available is this:

 - angularjs/angular
 - angularjs/angular-animate
 - angularjs/angular-cookies
 - angularjs/angular-dragdrop
 - angularjs/angular-loader
 - angularjs/angular-mocks
 - angularjs/angular-resource
 - angularjs/angular-route
 - angularjs/angular-sanitize
 - angularjs/angular-scenario
 - angularjs/angular-sortable
 - angularjs/angular-touch
