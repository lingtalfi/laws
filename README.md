Laws
========================
2017-03-27 --> 2017-04-06


[![laws.jpg](https://s19.postimg.org/an7lz8jqb/laws.jpg)](https://postimg.org/image/j5h23kq8v/)


Laws is an MVC system.


It has two parts, and you can implement one, the other, or both:

- laws one: not related to the web assets
- laws two: related to the web assets




Laws ONE
==============

It works with the following concepts:

- view
- theme
- layout
- widget
- position
- laws configuration file
- includes


And the variables below:

- themeName
- viewId
- widgetId
- widgetName
- widgetVariationName
- widgetTemplateName
- positionName
- positionVariationName
- positionTemplateName
- layoutName
- layoutVariationName
- layoutTemplateName
- includePath




Concepts
============



view
-------

A website is composed of pages.
Each page can be considered as a **view**.

A view displays a fully configured **layout**.

The configuration of a layout is done from **laws configuration files** (aka configuration files).



theme
--------
A theme is like clothes for your website.
It's basically a simple string, but you change it, it changes the look'n'feel of the website.





layout
--------
A layout holds the structure of a page.

It is represented by the mean of a template file.
Inside a layout template file code, two methods are available:

- widget ( $widgetId ): which renders the widget identified by $widgetId
- position ( $positionName ): which renders all widgets bound to the position $positionName



widget
--------
A widget brings functionality to a page.
It is placed on a page.

It is represented by the mean of a template file.
Inside a widget template file, two methods are available: widget and position (same as those for the layout)



position
--------
A position represents a position of the layout.
Basically, a position is a widgets group.

It wraps a group of widgets.

It is represented by the mean of a template file.
Inside a position template file, we have access to an array of the widgetIds for the given position.



laws configuration file
-------------------------

A laws configuration file (aka config file) defines the full configuration for a layout. 

It has the following structure:

- layout
    - tpl: $layoutTemplateName
- widgets
    - $widgetId:
        - tpl: $widgetTemplateName 
- ?position: this key is optional
    - $positionName:
        - tpl $positionTemplateName



includes
-------------------------


When you are creating multiple pages (or views), include is your best friend.
It basically gives you the ability to re-use any part of your layout in other layouts.

In other words, thanks to includes, you can factorize your layout in parts which make sense to you.


Includes are located in the **app/theme/$themeName/includes** directory, so that you can quickly answer the question: where are the includes?

Do you know the php include function?
That's exactly the same mechanism here, except that the include directory is set for you.






Variables
============


themeName
-------------
The name of the theme.




viewId
-----------
The viewId identifies a view, the viewId is used to identify a specific laws configuration file.
In other words, by choosing the viewId, you define exactly how the page will render.


widgetId
-----------
A widgetId is an identifier that uniquely identifies a widget inside a given layout.
By convention, if a widget is bound to a position, the widgetId starts with the $positionName (followed by a dot).
 
The widgetId is used inside template files, to call a widget, or internally to collect all widgets bound to a given position.


widgetName
----------------
widgetName is the common/human name of the widget.
For instance, the Hamburger widget.



widgetVariationName
---------------------
A widget can have many variations (that's what happens when a widget author is inspired).
We shall be able to identify each variation, and so the widgetVariationName does that. 


widgetTemplateName
---------------------
The widgetTemplateName is the combination of the widgetName and the widgetVariationName (separated with a slash).
It's used to identify a widget template file from a loader's perspective. 



positionName
----------------
positionName is the common/human name for a position (the template file of a position, which wraps a group of widgets).
For instance, the top position.


positionVariationName
---------------------
A position can have many variations (that's what happens when a position author is inspired).
We shall be able to identify each variation, and so the positionVariationName does that. 


positionTemplateName
---------------------
The positionTemplateName is the combination of the positionName and the positionVariationName (separated with a slash).
It's used to identify a position template file from a loader's perspective. 



layoutName
----------------
layoutName is the common/human name of the layout.
For instance, the Main layout.



layoutVariationName
---------------------
A layout can have many variations (that's what happens when a layout author is inspired).
We shall be able to identify each variation, and so the layoutVariationName does that. 


layoutTemplateName
---------------------
The layoutTemplateName is the combination of the layoutName and the layoutVariationName (separated with a slash).
It's used to identify a layout template file from a loader's perspective. 




includePath
----------------
includePath is the relative path, from the includes directory to your include file.





Laws TWO
==============
This is a suggestion for organizing web assets.
Basically, there is one stylesheet per layout variation,
then one per widget variation, then one for the user (to fix or supervise other stylesheets).

Also, each widget (or layout or position) has its own dedicated folder for assets.
So, in the widget css directory, you also can put your images for instance.






Snippets
===============

```php
<?php


$conf = [
    "layout" => [
        "tpl" => "landpage/default",
    ],
    "widgets" => [
        "main.any" => [
            "tpl" => "exception/default",
            "conf" => [
                "displayMode" => "trace",
            ],
        ],
    ],
];
```



Naming suggestions
====================
For viewIds, use simple page names: maintenance, error, productPage (instead of module prefixed names like MyModule_maintenance, HerModule_error, ...).
Multiple modules providing the same viewId should be because you have the option of which module to choose,
not because there is a semantical conflict.











Related
------------
Laws is implemented in the [Kamille](https://github.com/lingtalfi/Kamille) framework. 
 
 

