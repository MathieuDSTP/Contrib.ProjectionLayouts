# Orchard Projection Layouts

This module adds two new types of layouts to the Projections feature, _Raw Layout_ and _Shape Layout_.

## Raw Layout

This is a generalization of the _List Layout_ and lets you define a specific HTML tag for the container and also for each item in the list.

Besides, you can decide to inject some custom HTML at the beginning or at the end of the list, and also between the items.

## Shape Layout

The only option it lets you define is the name of a Shape. This shape will be used to render the layout. Usually you will like to create a custom template for this shape.

For instance, if you call the shape _Foo_ then you can create a file name `Foo.cshtml` in your theme to render the items.

Inside the template you have access to `Model.ContentItem` which contains all the content items returned by the projection.

You can also request the configured shapes by invoking the `Model.BuildShapes` member as a function, which will build the display for each result of the projection.

Example:

    @{
        var buildShapes = Model.BuildShapes;
    }

    <div class="row">
    @foreach (dynamic shape in buildShapes()) {        
        @Display(shape)    
    }
    </div>
