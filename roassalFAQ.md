# ROASSAL FAQ

* How does ROForceBasedLayout work?
- How can I zoom to fit?
  - You can't presently. Use a MiniMap.
- How do I interactively update a Mondrian view? (add/remove elements)
  - Don't. Use Roassal directly.
* Why is there no ROView>>#+ shortcut for #add:?
- How do you make the canvas (background) draggable?
  - view @ RODraggable

# Bugs

- withText doesn't put the text inside an element as shown in the Mondrian chapter

# Cookbook
- move an element with translateTo: or translateBy:
- get a minimap
  - view raw @ (ROMiniMap new targetView: view stack).

# Exercises
- object browser
- polymorphism visualization
- generalize TS Matrix visualization for other comparisons
- moose data visualization
- TestSurgeon visualizations (matrix done; graph todo)
- pong (abandoned)

# Summary

A Roassal visualisation consists of *components* displayed on a *view*.
Components are (usually?) *elements* or *edges*.
An element has a *model* (domain objects) which can consist of any Smalltalk objects.
The element will typically display some selected metrics of its model.
An element has one or more *shapes* which determine its visual display.
Shapes are added using addShape: or the + message.
To make an element react to events, a callback may be bound to an event.
Instead of manually writing callback blocks, prep-packaged *interactions* may be used. They are bound to an element with the @ message.
The argument to + or @ may be a class (subclass of ROShape or ROLayout), or an instance, in case default values are to be overridden.
Views with multiple elements can be have a *layout*.
Elements may be nested and contain a tree of *children*.

# Animation

This does not move the ball 2@3 2000 x -- it moves it 2@3 in 1/2000 increments!

  ROLinearMove new nbCycles: 2000; for: ball by: 2@3.

# Broken stuff
- Preambule
- ROScrollbable
- ROLinearMove comment is broken

---

# How to run TestSurgeon

* NB: Not working

- install Spy from STH

MCHttpRepository
	location: 'http://smalltalkhub.com/mc/ObjectProfile/Spy/main'
	user: ''
	password: ''

- load: SpyCore, Spy, ConfigurationOfSpy
- then install Roassal (if needed)
- install TestSurgeon

MCHttpRepository
	location: 'http://smalltalkhub.com/mc/PabloEstefo/TestSurgeon/main'
	user: ''
	password: ''

- TSBrowser example
