---
category: reference
---

Pablo also has an assortment of methods for changing the properties of 
svg nodes.

Changing a nodes attributes
---------------------------

The `attr()` method can be used to set or get an objects attributes.

To add one or more attributes pass in an object map of the attribute name and 
its value.

Specifying an attribute already set on that node will replace it.

    var square = Pablo.rect({width: 100, fill: 'red'});

    // Add a height and replace the fill color
    square.attr({height: 100, fill: 'green'});

    Pablo($output[0]).root({height:100})._(square);

To remove an attribute use `removeAttr()` and pass the attribute name as a 
string.

    var square = Pablo().rect({width: 100, height: 100, fill: 'red'});

    // Remove the fill attribute (turns out black by default)
    square.removeAttr('fill');

    Pablo($output[0]).root({height:100})._(square);

CSS styles can be applied
-------------------------

Appending a `style` element to the related svg node and changing its content 
with `content()`.

    // Create the root node.
    var paper = Pablo(document.body).root({width:300, height:420})

    // Append <style> element
    paper.style()
        // Change text content of style
        // (Similar to jQuery's text() method)
        .content(
            '* {stroke-width:20}' +
            'text {font-family:sans-serif; font-size:16px}'
        );
    ])

Making svg nodes hyperlinked
----------------------------

Pablo's `a(options)` method can be used to set up hyperlinks on svg elements.

Take note of the order of the chained function calls and how only the 'text' 
svg element is hyperlinked.

`a()` is only applied to multiple proceeding appended elements.

    var paper = Pablo($output[0]).root({height: 130});

    paper
    ._('circle', {cx:60, cy:60, r:50, fill:'#f33', stroke:'#050'})
    .a({
        _link: 'https://github.com/dharmafly/pablo',
        target: '_blank'
    })
    ._('text', {
        _content:'we ♥ pablo',
        x:220,
        y:30,
        fill:'#777',
        transform:'rotate(-45 300 170)'
    })
    ._('circle', {cx:260, cy:60, r:50, fill:'#3f3', stroke:'#050'})