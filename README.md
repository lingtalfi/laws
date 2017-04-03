Laws
========================
2017-03-27 --> 2017-04-03


[![laws.jpg](https://s19.postimg.org/4ms8rn23n/laws.jpg)](https://postimg.org/image/wa4y5qna7/)


Laws is an MVC system.



It works with the following concepts:

- view
- theme
- layout
- widget
- position
- laws configuration file


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
    - name: $layoutTemplateName
- widgets
    - n:
        - id: $widgetId 
        - name: $widgetTemplateName 
- ?position: this key is optional
    - $positionName:
        - name $positionTemplateName





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











Related
------------
Laws is implemented in the [Kamille](https://github.com/lingtalfi/Kamille) framework. 
 
 

