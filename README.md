# talk-react-shouldcomponentupdate


### shouldComponentUpdate

We all want to build super fast applications

We use react for that

### The biggest win!

Where can we find the bigger performance win in out React apps?

Before we start is interesting to think...

What's the most important part of a react Component? (render)

> Next slide 

Who here know how render works?

> Next Slide

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

### shouldCompoentUpdate (all the things)

This function os going to determine whether or not your render function will call.

### shouldCompoentUpdate (not really...)

We should use `shouldComponentUpdate` whenever we need it, it's not for every case.

### shouldCompoentUpdate

Very sadly this is the default behaviour of  this function.

> Next slide

shouldComponentUpdate(nextProps, nextState) {
  return true;
}

This is going to call render any time you get a new state or props.

Even if this change was relevant or not to that component.

### Stateless components

They update/render every time.

### The fastest

Let's see what's the fastest.

> Next slide

Here we have three different types of components.

Stateful / Stateless / Statefull + shouldComponentUpdate

> Next slide

Turns out that in react 15 is faster on rendering all of them.

But the fastest is the Pure component

Why pure are faster than stateless??? (We have been hearing this for really long...)

Because ones it's rendered, react doesn't need to render it again, so updates are faster.

and...

> Next slide

As Dan Abramov says, there is no optimazation for stateless, they are wrapped in a class and follow the same code path.


### The simplest trick

Is to know when to render and when not to render.

shouldComponentUpdate is your friend, so use it.

Don't use stateless components if you can optimize it with `shouldComponentUpdate`

> Next slide

If we follow this pattern we send less changes to react, so at the end DOM manipulation will be less, and we let the browser do more things at the time.

[DEMO TIME] (Checkbox at Live Nation Subscriptions)

### How do we get the ideal update?

We want to return false from shouldComponentUpdate as high up in your application as you can.

1. Make shouldComponentUpdate check fast (if that's slow, there is no point on doing it)
2. Make shouldComponentUpdate check easy (more for us as developers, than for react)

### Make shouldComponentUpdate check fast

You don't want to check all the data al the way down, because it's too expensice and you kind of lose that speed that `shouldComponentUpdate` brings you.

### Changing references

The way you want to do it here is checking **references equality**.

We are going to treat an object as changed if its reference is not longer the same.

So if the object satisfies that triple equal check then we are not going to render that component.

> Next slide

So in the context of redux reduccers, if you like to update a single item of a collection,

Loop over them, and check if thats' not the id you want to update, return the same reference.

Otherwise, return a new object with the changes.

By doing that, in your `shouldComponentUpdate` you can just do shallow comparasons.

> Next slide

So you do one level deep check.

This should be almost everywhere as simple as that.

As I said before, we treat changing value as change reference.

### Make shouldComponentUpdate check easy

This is a picture of our state.

[Explain state]

But there are some problems with it.

> Next slide

Huge `shouldComponentUpdate` functions: 

Where we need to check if objects are the same and then if interaction changes.

So it become bigger even this is not a big state tree.

Tight coupling of parents:

Where components should know less about each other.

Change can be done from children without the parent knowing about it.

So how can we solve that.

> Next slide

Denormalizing your data.

[Explain state]

Structuring your data in this way your itam can access the property so, it can be modified from the children.

> Next slide

### Takeaways

Read...

### ideal update

In that way we can get the ideal update.
