# 03-PIZZA_MENU

- import React from "react"; # add react to index.js
- import ReactDOM from "react-dom/client"; add react-dom to index.js

```
function App() { # create component
    return <h1>Hello React!</h1>;
  }
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## Components

- never nest the function declaration, and always declare components in top level
- but use nested component like bottom:

```
function App() {
  return (
    <div className="container">
      <Header />
      <Menu />
      <Footer />
    </div>
  );
}

function Footer() {
  return (
    <footer>{new Date().toLocaleTimeString()}. we are currently open</footer>   # in {} we can write javascript code
  );
```

## JSX

- Declarative syntax
- components must return block of JSX
- extension of javascript that embed CSS, JavaScript and React into HTML
- each JSX element coverted to a React.createElement function call

- React separate conserns by separate components instead of separate html, css, javascript

## Add Style

- import css file to any file you want
- add class of style to your tags:

```
<div className="container">
```

## Props

- we can pass data from parent components to child components
- App -> Menu -> Pizaa

```
function Menu() {
  return (
    Pizaa
    name="Pizza Funghi"
    ingredients="Tomato, mushrooms"
    price={12}
    photoName="pizzas/funghi.jpg"
\  />
  );
}
```

- pass it to pizza component:

```
function Pizaa(props) {
  return (
    <div className="pizza">
      <img src={props.photoName} alt={props.name} />
      <div>
        <h3>{props.name}</h3>
        <p>{props.ingredients}</p> # write javascript syntax in {}
        <span>{props.price}</span>
      </div>
    </div>
  );
}
```

- style = {} and write javascript syntax in {} -> <h1 style={{color:red}}></h1>

* 2 features of react: about data:

1. props are read-onky and immutable
2. data just can be access from parant to childs and does not possible pass from child to parent

- props -> is data comming from outside, and can only be updated by parent component
- state -> state is internal data that can be updated by the component's logic

## Destructuring props

```
function Footer() {
    <footer className="footer">
      {isOpen && <Order openHour={openHour} closeHour={closeHour} />}
    </footer>
  );
}

function Order({ closeHour, openHour }) { # destructuring props
  return (
    <div className="order">
      <p>
        We're happy to welcome you between {openHour}:00 and {closeHour}:00.
      </p>
      <button className="btn">Order</button>
    </div>
  );
}
```

- loop rendering:

```
function Menu() {
  return )
      <ul className="pizzas ">
        {pizzaData.map((pizza) => ( # map on pizzaData list
          <Pizaa pizzaObj={pizza} key={pizza.name} /> # pass pizzaObj as props into Pizza component
        ))}
      </ul>
  );
}


function Pizaa(props) {
  return (
    <li className="pizza">
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
    </li>
  );
}
```

in javascript mode {}, the expretion must produce value

- use conditional phrases for sett css class for each block of jsx:

```
<li className={`pizza ${pizzaObj.soldOut ? "sold-out" : ""}`}>
```

## React Fragment

- use <></> for grouped some elements without get them to one one element, they have been seprate
