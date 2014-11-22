# Views

At this point you should have created a module, attached it to an area in the backend and integrated the render code into the template files.

#####Good to know
The whole internal view concept is

a) optional to use  
b) based on the awesome Twig library

####Creating template files for our module

We've added two areas and configured our input form to show different inputs depending on where the module is attached.  
Different inputs mean different data, so it makes sense to have different templates as well – one for each area context / dataset.

We will create the templates inside of the root directory of the module, which should be: /modules/ModuleDemoEditor/

Create two files in the modules directory:

1. \#normal-default.twig
2. \#side-default.twig

You can replace 'default' with whatever you like, it's not important for our example. '#normal' and '#side' is the naming convention to create area-context sensitive templates.  
The ViewLoader will now find exactly one template per context, and it will automatically use that one.


####Template content

Finally we are going to print something to the screen.  
Open up '#normal-default.twig' and paste the following:

```
{{ Model.democontent | raw }}```

in '#side-default.twig' use the other fields key:


```
{{ Model.democontent_alt | raw }}```


That's it basically, but there is more:


#####Special return objects

You might have noticed the `returnObj' => 'Element'` setting in the fields definition.  
This tells the plugin to create a special object while preparing the fields for frontend output.

If no `returnObj` is set, the data of the fields key would be (more or less) the raw data which was entered. 
We've set it to 'Element' which is a special object to enable inline editing for this field resp text based fields in general.  
Inline editing needs some special markup and the object will take care of it for us.

So, let's make our data editable by extending what we already have:

```{{ Model.democontent.el('div').html() | raw }}```

`el()` is a special method of the 'Element' return object and sets the wrapper element, which we need for tinyMCEs inline mode.

`html()` is the output method which prints the result.

There are some other methods like `addClass()` and `addAttr()` but we don't need them for now.

Return Objects are not exclusivly used to make things editable.  
You can create your own return objects and add whatever useful functionalities you need to work with field data.


