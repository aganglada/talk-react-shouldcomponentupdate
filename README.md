# talk-react-shouldcomponentupdate


### shouldComponentUpdate

We all want to build super fast applications
We use react fro that

### What is the biggest win we can get for our react apps?

Before we start is interesting to think...
What's the most important part of a react Component?
Who here know how render works?

### Initial render

[initial change image]
This is the initial render of a react application.
Here we have our tree of components.
That might not look like your tree, it doesn't matter.
Green means it has updated and rendered.

### Proposed change

[proposed change image]
Let's say we want to update an element of this component which is only relevant to this one node.

### Ideal update

[ideal update image]
This is what we want, this is an ideal update.
We don't want anything else to change.

### Default behaviour

[default behaviour image]
But by default this is what happen in a react app.
This is the biggest performance problem in our react apps.
Even if react algoriddim work really good on diffing your dom.
The reason for this is any component that is going to render when it shouldn't be is causing performance problems.
And we want to stop that up in the highest level as we can.

### shouldCompoentUpdate

[shouldComponentUpdate]
This function os going to determine whether or not your render function will call.

### shouldCompoentUpdate

[shouldComponentUpdate]
Very sadly this is the default behaviour of  this function.

shouldComponentUpdate(nextProps, nextState) {
  return true;
}

This is going to call render any time you get a new state or props.
Even if this change was relevant or not to that component.

[stateless functions]
They update every time.

### performance

...

### How do we get the ideal update?

We want to return false from shouldComponentUpdate as high up in your application as you can.
1. Make shouldComponentUpdate check fast
2. Make shouldComponentUpdate check easy

### Make shouldComponentUpdate check fast

Example of deep checking

### Changing references

The way you want to do it here is checking references equality.
If his reference has change then we update.

### Fast reference checking

isShallowEqual

### Make shouldComponentUpdate check easy
denormalization of the state

### ideal update

In that way we can get the ideal update.

[DEMO TIME]