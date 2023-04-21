202207140132
Tags: #recetas

# useReducer en lugar de useState

## Pasos 
1. Importar React y hooks, `useReducer` en lugar de `useState` ([[useState con createContext y useContext |receta con useState]]).
2. Definir el estado inicial `initialValue`
3. Definir la logica de actualización de estado en una funcion `reducer` la cual recibe el `state` y las `action`.
	1. Dentro de la función revisar el `action.type` dentro de un `switch`
	2. En cada caso ej. `ICREMENT` o `DECREMENT`, regresar el `...state` y el nuevo estado.
4. Definir un custom hook para usarse en un provider (`useValue`) que utilice `useReducer` en lugar de. `useState` y le pasamos la funcion `reducer` y el estado inicial `initialValue` 
5. Este paso lo repetimos como en [[useState con createContext y useContext]]
	1. Crear un contexto con `createContext` con un valor inicial de `null`.
	2. Crear `useGlobalState` custom hook que regrese el valor del contexto. En este hook revisamos si el Provider funciona como esperamos.
	3. Necesitamos un context provider `GlobalProviderState` que reciba un `children` y regrese el `Context.Provider` con el `value` asignado a `useValue()`
6. En los event handler de lo elementos del DOM ejecutar la funcion `dispatch` la cual envia el tipo de accion. ej. `{ type: 'INCREMENT' }`
7. Envolver el componente en el context provider `GlobalStateProvider`
8. No olvides exportar el componente con `expor default Component`

### Ejemplo

```js
import React, { createContext, useContext, useReducer } from 'react';

  
const initialState = {
	count1: 0,
	count2: 0,
};

const reducer = (state, action) => {

switch (action.type) {
	case 'INCREMENT':
		return {
			...state,
			[action.name]: state[action.name] + 1,
		};
	case 'DECREMENT':
		return {
			...state,
			[action.name]: state[action.name] - 1,
		};
	default:
		return state;
	}
};

  
const useValue = () => useReducer(reducer, initialState);

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
	const [state, dispatch] = useGlobalState();
	
	return (
	
		<div>
			{state[name]}
			<button 
			onClick={() => dispatch({ type: 'INCREMENT', name })}>+1</button>
			<button onClick={() => dispatch({ type: 'DECREMENT', name })}>-1</button>
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
	</GlobalStateProvider>
);


export default App;
```
