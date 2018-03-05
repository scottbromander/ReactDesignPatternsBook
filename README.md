# React Design Patterns and Best Practices

[Link to book](https://www.packtpub.com/web-development/react-design-patterns-and-best-practices)

## Chapter 1 - Declarative Programming

### Imperative Programming versus Declarative Programming

- Imperative Programming, describes how things work. Think OOP.
- Declarative Programming, describes what you want to achieve. Think Functional.

Imperative, at the bar:
- "Bartender",

- "Go to the shelf",

- "Put a glass down in front of the draft",

- "Pull down the handle until the glass is full",

- "Pass the glass to me"

Declarative, at the bar:
- "Bartender, beer please!"

The declarative example works assuming the Bartender knows what you are talking about.

```
.toLowerCase(["FOO", "BAR"]);

//Imperative approach
const toLowerCase = input => {
    const output = [];
    for(let i = 0; i < input.length; i++){
        output.push(input[i].toLowerCase());
    }
    return output;
}

//Declarative approach
const toLowerCase = input => input.map(
    value => value.toLowerCase();
)
```

The goal of Declarative programming is for the developer to describe what they want to do
and there is no need to list all the steps to make it work.

React offers a declarative approach making it easier to use.

### React Element

.createClass or extending {Component}, you are creating a component.

React manages all the components at runtime. You can absolutely have more than one of the
same components at the same time.

There is no need to tell React how your components should interact with the DOM, React manages this for us.
You declare what you want and React has got it from there.

This is the opposite of other libraries, such as jQuery. You need to manage the creation, update, and
destruction of DOM elements manually.

React elements describe what should be on the screen. These are immutable objects, which describe the element
with Javascript without actually being the element themselves (Virtual DOM).

Example of an element
```
{
    type: Title,
    props: {
        color: 'red',
        children: 'Hello there'
    }
}
```

Elements have type, which is the most important attribute, as well as properties.
Children are optional.

Type tells React how to deal with the element itself.

DOM elements and components can be nested inside of eachother.

Example:
```
{
    type: Title,
    props: {
        color: 'red',
        children: {
            type: 'h1',
            props: {
                children: 'Hello, H1!'
            }
        }
    }
}
```

When the type of the element is a function, React calls it, passing the props to get back the
underlying elements. It keeps on performing the same operation recursively on the result
until it gets a tree of DOM nodes, which React can render on the screen. This process is
called `reconciliation`, and it is used by both React DOM and React Native to create the user
interfaces of their respective platforms.

### Unlearning Everything
React can be tricky because it forces developers to not follow common thought patterns, such as 'seperation of concerns'.
We can see this in our use of jQuery and even Angular. View and Logic are two different things. One updates the other.
In React, they are much more tightly coupled. 

But the truth is that the separation of concerns was a bit of an illusion. 

If you look at a Templating engine (let's say Handlebars), you notice that some logic like loops make it into the DSL
(Domain Specific Language). 

React tries to take a step and puts templates where they belong, next to the logic. React tries to get everything organized
into small bits of functionality called `components`. 

A framework should not tell you how to separate concerns, because each application has their own. Only the developers should decide how to limit the boundries of the applications they are developing. 

Component-based development changes the approach drastically for the way we write web applications.

Example component's render method:

```
render() {
     return (
       <button style={{ color: 'red' }} onClick={this.handleClick}>
         Click me!
</button> )
}
```

"The best way to learn a new framework is to build small projects", totally agree.

Another difficult pill to swallow is moving Styling into the component as well. The end goal is to perfectly encapsulate a component to live by itself. 

Example:
```
var divStyle = {
     color: 'white',
     backgroundImage: 'url(' + imgUrl + ')',
     WebkitTransition: 'all', // note the capital 'W' here
     msTransition: 'all' // 'ms' is the only lowercase vendor prefix
};
   ReactDOM.render(
    <div style={divStyle}>Hello World!</div>,
    mountNode
);
```

`#CSSinJS`, covered more in Chapter 7

## Common Misconceptions

The first is that it takes a ton of code to get a simple React project up and running (Note, I know where the author is going with this, and I do not agree. They are about to go down the `'type="text/babel"'` and `create-react-app` route, which is good for toy apps, but does not seem to be good for production)

The argument that is being made here, is that the project should only start to pull in dependancies as you need them. Which obviously I do not disagree with, but if you have desigend your application ahead of time, you should know how to handle each of these challenges. Setting up the project, getting the builders up and running, pulling in the tools, and so on, should really be done right away (in my opinion). That way the team is all working with the same tooling and not everyone needs to know the entire setup and build process. Keep people focused in their discipline is important. -Personal opinion, `</rant>`


