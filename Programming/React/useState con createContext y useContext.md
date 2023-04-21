202207140100
Tags: #recetas 

### useState con createContext y useContext

#### Pasos

1.  Importar React y hooks para crear un Context `createContext`, `useContext`.
2.  Definir el estado inicial `initialState`
3.  Define un custom hook para usarse en un provider (`useValue`) que utilice `useState` con el estado inicial definido.
4.  Crear un contexto con `createContext` con un valor inicial de `null`, el cual sera reemplazado por `useValue`.
5.  Crear `useGlobalState()` custom hook que regrese el valor del contexto. En este hook revisamos si el Provider funciona como esperamos. No es actualizado porque `useValue()` nunca regresa `null`.
6.  Necesitamos un context provider `GlobalStateProvider` que reciba un `children` y regrese el `Context.Provider` con el `value` asignado a `useValue()`. Debe de ponerse cerca de la raiz.
7.  Construye un componente donde se controle el estado con `useGlobalState()` en lugar de `useState`.
    1.  Asignar los elementos en el DOM con un event handler `onClick`, el cual ejecutara funciones que modifican el estado `...state`
    2.  Las funciones utilizan `setState` el cual tiene asignado `useGlobalState` y recibe 3 parametros (`..state`, `[name]`, )
8.  Envolver el componente en el context provider `GlobalStateProvider`.
9.  No olvides exportar el componente 🚀

### Ejemplo

```js
import React, { createContext, useContext, useState } from 'react';

const initialState = {
	count1: 0,
	count2: 0,
	count3: 1,
};
const useValue = () => useState(initialState);
const Context = createContext(null);

const useGlobalState = () => {
	const value = useContext(Context);
	if (value === null) throw new Error('Please add GlobalStateProvider');
	return value;
};
  
const GlobalStateProvider = ({ children }) => (
	<Context.Provider value={useValue()}>{children}</Context.Provider>
);

const Counter = ({ name }) => {
	const [state, setState] = useGlobalState();
	const count = state[name] || 0;
	const increment = () => {
		setState({ ...state, [name]: count + 1 });
	};
	
	const decrement = () => {
		setState({ ...state, [name]: count - 1 });
	};
	
	return (
		<div>
			{count}
			<button onClick={increment}>+1</button>
			<button onClick={decrement}>-1</button>
		</div>
	);

};

  
const App = () => (
	<GlobalStateProvider>
		<h1>Count1</h1>
		<Counter name="count1" />
		<Counter name="count1" />

		<h1>Count2</h1>
		<Counter name="count2" />
		<Counter name="count2" />

		<h1>Count3</h1>
		<Counter name="count3" />
		<Counter name="count3" />
	</GlobalStateProvider>
);
```