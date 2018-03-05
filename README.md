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

