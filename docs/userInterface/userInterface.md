# UI Standartization
Product UI Standard goes beyond styles of elements.

Product UI Standard must address three fundamental problems:
1. How User works with Collections of Application Entities?
2. How User works with Individual Application Entity?
3. How User provide Input Data for Application Services?
4. How User works with Application Event Collections?

## Standartizing Entity Collections Views (Collection Page)
All your collections must share the same UX, regardless the Entity you show.

You need to create the following UI mocks:
1. Basic Collection view, not bound to specific Entity.
2. Collection Toolbar
    1. Search Entities
    2. Filter by different Entity Attributes
    3. Sort and change sort order
3. Add to Collection operation.
4. Delete Entity from Collection operation.
5. Open Entity Details operation.

## Standartizing Individual Entity Views (Details Page)
All you Details pages must share the same UX.
Regardless of the Entity type, User must be able to
1. Find the common properties at the same locations. Like, any entity has name, description,
creation date. Almost any has updated date. All these properties must be shown at the same
location of details page, regardless the Entity type.
2. Find the custom properties at the same locations.
3. Find the collections of embedded entities at the same location.

So Details page can be split to several zones, and User must be able to navigate freely 
between each of them, staying inside the Details page:
1. Zone to show Common Entity Properties. It __must__ be the same for all your Entities.
2. Zone to show Custom properties of a simple data types: like Number or String
3. Zone to show the Custom property of a Custom Type.
4. Zone to show the Custom property which is embedded Collection of Custom Type.

Now, you can mix this four zones in whatever layout you want.

## Standartizing User Input UI (Form Views)
Users will input data to your Application via UI forms.

And guess what, you have at least the following options to support this:
1. Modal Form.
2. Single Page Form.
3. Multi Page Form.

Ideally, you need to choose __ONE__.

__Why?__

Your Users will have smooth similar UX while filling your forms.
And it save you a lot of development effort on front end.
Imagine, all this stuff will need validation and error reporting.

How to choose one or another for your project?

Think bigger, than your current release. Ask you product manager about the plans for future.

The key questions are:
1. Will User have to enter more than 3-4 fields in one form? If yes, then your Modal option
is not an option.
2. Next, will User have to enter more than 2-3 groups of form fields?.
E.g. you want User to fill the Personal Info and Address and Company Info in registration form.
If yes, you better use Multi Page Form instead of Single Page Form. But still, Single Page Form
will work.
3. Next, will User have to enter fields in one group, that will define the next group of 
fields to enter?
E.g. you want User configure the Event and you want him to select the type of Action to configure.
Each Action has different set of fields to configure.
If yes, then Multi-Step form is the best friend for you.

Now, if you though of all possible scenarios of future development and you foresee your Users entering
just a few fields and click Submit. => Modal is your best friend.

A few groups of fields, no bound logic, when values in one group define the next group? => Single Page
Form.

More that 3 groups, bound by logic => Multi Page Form.

If your product is for Enterprise - do not even think. Multi Step Form is your choice.

## Standartizing Events View
You may need to show the Events in your Application.

At this point remember, that Event's main property is that, hm, it is time bound.

Another thing is that Event is IMMUTABLE.

Never mix Events and Entities in the same view.

Collection of Entities is not Event Timeline.

Entities are mutable, Collections of Entities are sortable by different properties.

Collections of Events are time sorted. Sorting events by any other property does not make sense.

Collection of Entities is viewed to find one and do something with it.

Collection of Events is viewed to find some correlations between different Event Types.

Hence you choice for Event View may be Vertical Timeline with most recent Events at the top.

Or separate Timelines for each Event Type to solve correlation problems.

Or Horiziontal plot with time as X axis and Event Types as labels on Y axis.

Pick one for your view. Don't add complexity, when you don't need Event correlation. Go with
simple Timeline.

But if you do need correlation, use the same visuals for both simple Timeline and Correlation.