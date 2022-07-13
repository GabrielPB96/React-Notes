# REACT

Es declarativo, basado en componentes.

## Props
Propiedades del componente.

## State
Estados del componente.

## Componentes

Los componentes son una forma de agrupar elementos que se pueden reutilizar.

***Cada componente debe estar en un archivo aparte.***
    
**Como Funcion**

  ```javascript
  function MyComponent(props) {
    return <div>{props.name}</div>;
  }
  ```

**Como Clase**

  ```javascript
  class MyComponent extends React.Component {
    render() {
      return <div>{this.props.name}</div>;
    }
  }
  ```

## Props y State

### Props (Propiedades)

Las propiedades son valores que se pasan al componente, estos son agrupados en un objeto llamad props.

Este objeto es inmutable, es decir, no se puede modificar.


**Tipos de Propiedades**

- Strings
- Numbers
- Booleans
- Arrays
- Objects
- Functions
- React Elements
- React Components


```javascript
function MyComponent(props) {
  return <div>{props.name}</div>;
}
```

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return <div>{this.state.name}</div>;
  }
}
```

**Propiedades por Defecto**

  ```javascript
  MyComponent.defaultProps = {
    name: 'Default Name'
  };
  ```

```javascript
  <MyComponent
    name="My Name", //String
    age={42}, //Number
    isMarried={false}, //Boolean
    //Object
    address={{
      street: '123 Main St',
      city: 'Anytown',
      state: 'California'
    }},
    elementReact={<div>Hello</div>}, //React Element
    functionReact={() => {}}, //React Function
    componentReact={<MyComponent/>}, //React Component
  />
```

> nmp i -S prop-types

[prop-types](https://www.npmjs.com/package/prop-types)

### State (Estado)

Son valores que se actualizan en el componente, estos son agrupados en un objeto llamado state.

**Caracteristicas**

- Inmutable.
- No se puede modificar directamente.
- Es asincrono.

Para modificar el estado se utiliza el método setState().

**Como Clase**

```javascript
import React, { Component } from 'react';
class MyComponent extends React.Component {
  //pasarle los props al constructor
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial Name'
    };
  }

  render() {
    return <div>{this.state.name}</div>;
  }
}
```

- **setState()**

```javascript 
this.setState({
  name: 'New Name'
});
```

### Renderizado condicional

```javascript
import React, { Component } from 'react';

function Login() {
  return(
    <div>
      <h1>Login</h1>
    </div>
  );
}

function Logout() {
  return(
    <div>
      <h1>Logout</h1>
    </div>
  );
}

export default class MyComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      isLoggedIn: false
    };
  }

  render() {
    return (
      <div>
        <h2>Renderizado condicional</h2>
        {this.state.isLoggedIn ? <Login/> : <Logout/>}
      </div>
    );
  }
}
```

### Renderizado de Elementos (Listas)

Cada elemento debe tener una clave única.
  
  ```javascript
  import React, { Component } from 'react';
  export default class RendElementos extends Component {
    constructor(props) {
      super(props);
      this.state = {
        seasons: ['Spring', 'Summer', 'Fall', 'Winter']
      };
    }

    render() {
      return(
        <div>
          <h2>Renderizado de Elementos</h2>
          {
            this.state.seasons.map((season) => <li>{season}</li>)
          }
        </div>
      );
    }
  }
  ```
  ***Warning: Each child in a list should have a unique "key" prop.***
  
  ```javascript
  
  ``javascript
    {
      this.state.seasons.map((season, index) => {
        return <likey={index}>{season}</li>;
      })
    }
  ```

  ### Eventos y Bindings
  
  ```javascript
  <button onClick={myFunction}>Click Me</button>
  ```

  ```javascript	
  import React, { Component } from 'react';
  export default class MyComponent extends Component {
    constructor(props) {
      super(props);
      this.state = {
        contador: 0
      };

      //Cuando se hace componentes con clases.
      this.sumar = this.sumar.bind(this);
      this.restar = this.restar.bind(this);
      //-----------------------------------------
    }

    sumar(event) {
      this.setState({
        contador: this.state.contador + 1
      });
    }

    restar(event) {
      this.setState({
        contador: this.state.contador - 1
      });
    }
    
    render() {
      return (
        <h2>Eventos y Bindings</h2>
        <button onClick={this.sumar}>+</button>
        <button onClick={this.restar}>-</button>
        <h3>{this.state.contador}</h3>
      );
    }
  }
  ```


