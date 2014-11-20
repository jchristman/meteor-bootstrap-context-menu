meteor-bootstrap-context-menu
=============================

This library is a meteor translation of the http://lab.jakiestfu.com/contextjs/ library, with some modifications made for convenience and for special features.

Installation
============

meteor add jchristman:context-menu

Defining the menu
=================

Define the menu as an object: this is a natural way of expressing the context menu. You can define an object with roughly this structure:

```
test_menu = [
    {
        header: 'Example'
    },
    {
        icon: 'glyphicon-plus',
        text: 'Create',
        action: function(e) { alert('Create clicked'); console.log(e); }
    },
    {
        icon: 'glyphicon-edit',
        text: 'Edit',
        action: function(e) { alert('Edit clicked on ' + this.innerHTML); }
    },
    {
        icon: 'glyphicon-list-alt',
        text: 'View Data As:',
        subMenu : [
        {
            text: 'Text',
            action: function(e) { alert('Text clicked on ' + this.innerHTML); }
        },
        {
            text: 'Image',
            subMenu: [
            {
                text: 'PNG',
                action: function(e) { alert('PNG clicked on ' + this.innerHTML); }
            },
            {
                text: 'JPEG',
                action: function(e) { alert('JPEG clicked on ' + this.innerHTML); }
            },
            {
                text: 'GIF',
                action: function(e) { alert('GIF clicked on ' + this.innerHTML); }
            }
            ]
        }
        ]
    },
    {
        divider: true
    },
    {
        header: 'Another Example'
    },
    {
        icon: 'glyphicon-trash',
        text: 'Delete',
        action: function(e) { alert('Delete clicked on ' + this.innerHTML); }
    }
];
```

There are several important features here. The "text" field will be the text displayed in the menu for that item. The "icon" field *requires* a glyphicon from bootstrap - you just need to tell it which glyphicon you want. Last, you can define an arbitrary depth menu by adding the subMenu field.

Binding the context menu
========================

A very simple example of this is shown.

```
context.attach('body', test_menu);
```

In this, we see that it is defining a context menu for the body element. This can be replaced with any jquery selectable element and it will work. 

Other Options
=============

For other options, see the documentation at http://lab.jakiestfu.com/contextjs/. There is very little different about this library.
