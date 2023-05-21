
### ¿Qué son los Hooks?

Los Hooks son funciones que permiten conectarse a funciones incorporadas en la librería de React. Los hooks dan la posibilidad de controlar el estado así como otras características dentro de nuestra aplicación.

#### **useState**

`useState` es el hook más común, se utiliza para mantener el estado dentro de un valor dentro de un componente (un componente puede tener varios hooks de estado). Este hook tiene la siguiente sintaxis:


```JSX
const [state, setState] = useState('This is my initial state');
```

Podemos inicializarlo con cualquier valor y utilizarlo dentro de nuestra aplicación. Y cada vez que necesitemos cambiar su valor, llamaremos la función setState y le pasaremos como parámetro el nuevo valor.

Es importante saber que setState es una función asíncrona, por lo tanto, si necesitas inmediatamente su valor para realizar otra operación, podremos acompañarlo con useEffect.

#### **useEffect***

`useEffect` es el segundo hook más utilizado dentro de React. Y, como se ha mencionado anteriormente, engloba las tres etapas del ciclo de vida de un componente. Este hook tiene la siguiente sintaxis:

```JSX
useEffect(() => {
	// Desired Effect
	
	return () => {
	
		// Cleanup
	}
}, [/* Dependency Array */]);

```

Cuando nuestro componente es montado, nuestro efecto será ejecutado; aunque, debemos tener en cuenta que los efectos secundarios no deben ejecutarse dentro del useEffect, esto puede llevar a un comportamiento extraño dentro de nuestra aplicación. Estos efectos pueden ser llamados dentro de nuestro useEffect y ser ejecutados en algún otro lugar de la aplicación.

En la sección de cleanup, deberemos cancelar todas las operaciones que hagan necesite nuestro componente. No debemos actualizar el estado, dejar `eventListeners` escuchando, operaciones asíncronas en proceso, etcétera. Cuando nuestro componente se destruya, se debe destruir todo lo que tenga relación directa a él.

Por último queda hablar sobre el arreglo de dependencias.

Dentro de este arreglo colocaremos todas las variables que queremos estar 'escuchando' y cada vez que cambie alguna de ellas, nuestro efecto será lanzado nuevamente.

Imaginemos un caso donde tengamos que hacer una petición a nuestro servidor con una url, podríamos hacerlo de la siguiente forma

```JSX
export const Component = ({ url }) => {
	const fetchData = (url) => {
		// Do Request
	}
	useEffect(() => {
		fetchData(url);
	}, [url]);
}
```

Y si te lo preguntas, también podemos colocar funciones dentro de nuestro arreglo, pero hay que tener cuidado, ya que, en el arreglo de dependencias estará la referencia a la función, y, al igual que los objetos, dos funciones pueden llamarse igual, realizar las mismas operaciones pero estarán ambas harán referencia a una ubicación de memoria distinta. ¿Por qué mencionamos esto? Porque, cada vez que el estado del componente cambia, las funciones también son creadas nuevamente y, por lo tanto, cambian de referencia; nuestro arreglo de dependencias nota el cambio y lanza nuevamente el efecto, y con esto, cayendo en un ciclo infinito.

Entonces, ¿cómo le hacemos para ejecutar funciones con efectos secundarios?

Hay dos principales maneras, la primera y más sencilla es mover la función dentro del mismo efecto, dejándolo de la siguiente manera:

```JSX
export const Component = ({ url }) => {
	useEffect(() => {
		const fetchData = (url) => {
			// Do Request
		}
		fetchData(url);
	}, [url]);
}
```

La segunda manera es memorizando la función con otro hook *useCallback()*, dejando nuestro código de la siguiente manera:

```JSX
export const Component = ({ url }) => {
	const fetchData = useCallback((url) => {
		// Do Request
	}, [url]);

	useEffect(() => {
		fetchData();
	}, [fetchData]);
}
```

  

#### **useContext**

`useContext` nos sirve para utilizar valores que se encuentren dentro del contexto actual. Devuelven el valor proveído por el mismo contexto (*React.createContext()*). Su sintaxis es la siguiente:

```JSX
const context = useContext(Context);
```

#### **useReducer**

`useReducer` brinda una alternativa a useState, se utiliza frecuentemente en combinación a el contexto de la aplicación. Es preferible usar *useReducer* cuando el estado tiene un valor complejo con múltiples subvalores.

  Su sintaxis es la siguiente:

```JSX
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

Acepta un reducer de tipo `(state, action)` y devuelve el estado actual junto con la función dispatch (la cual nos servirá para actualizar el estado de la aplicación).

Los reducers son funciones de que reciben el estado inicial y una acción a realizar; deben forzosamente regresar un estado de tipo `state` el cual puede variar (es lo que buscamos) dependiendo de la acción.

Veamos cómo luce un reducer 

```JSX
export const reducer(state, action) => {
	switch(action.type) {
		case 'logIn':
			return {
			...state,
			isLogged: true,	
			name: action.payload		
			}
		case 'logout':
			return {
			...state,
			isLogged: false,
			name: null
			}
		default:
			return state;
	}
}
```


Como puedes notar, nuestro reducer sólo tiene dos operaciones, para iniciar y cerrar sesión. Y también habrás notado que estamos pasando una copia al estado, esto no es necesario en este caso, pero es recomedable hacerlo para que siempre tengamos nuestro estado completo y evitar potenciales errores.

```JSX
export const Component = () => {
	const [state, dispatch] = useReducer(reducer, {
		isLogged: false,
		name: null
	});
	const { isLogged, name } = state;
	
	const logOut = () => {
		dispatch({
			type: 'logOut'
		});
	}
	const logIn = () => {
		dispatch({
			type: 'logIn',
			payload: 'Karla'
		});
	}

	return (
		{
			isLogged ? (
			<>
				<p>Welcome {name}</p>
				<button onClick={logOut}>Log Out</button>
			</>
			
			) : (
				<button onClick={logIn}>Log In</button>
			)
		}
	);
}
```

  
#### **useCallback**

```useCallback``` Antes de entrar a la utilidad de useCallback, es importante recalcar que, cada vez que se hace un re render en un componente, las funciones que lo componen son re creadas en un espacio de memoria distinto. Y si, este componente tiene componentes hijos que reciben esta función, aunque usen React.memo, volverán a renderizarse.

Esta es la solución de useCallback, memoriza una función para que ésta sea exactamente la misma en cada render. Su sintaxis es la siguiente



```JSX
const memoizeFunction = useCallback((params) => {
	// Do your Job!
}, []);
```

El arreglo de dependencias funciona prácticamente igual al de useEffect.

Pero, ¿qué pasa si queremos mandar un setState a nuestros hijos?, si nosotros hacemos usamos `useCallback` de la siguiente forma sería desaprovechar este hook, podríamos hacer que setState también use `useCallback` pero esto nos puede llevar a un *callback hell*.

```JSX
const [state, setState] = useState();
const memoizeFunction = useCallback((params) => {
	setState(params);
}, [setState]);
```

Es importante saber que setState nos retorna el mismo state, por lo tanto podemos utilizar `useCallback` de esta forma y obtener las operaciones deseadas.

```JSX
const [state, setState] = useState();
const memoizeFunction = useCallback((params) => {
	setState(state => params);
}, []);
```

  
#### **useRef**

`useRef` Lo más común en React es forzar un nuevo renderizado cuando queremos modificar algún elemento del DOM. Sin embardo, ¿cómo podemos hacer para hacer focus a algún punto, realizar alguna animación o reproducir algún archivo?

Para este tipo de casos es para lo que existe useRef. Este hook crea una referencia a un elemento del DOM que ha sido renderizado y a través de él permite ejecutar este tipo de acciones. Prácticamente podemos acceder a un elemento con JavaScript puro y sin necesidad de colocar ID's. Es bastante útil para realizar cambios que no necesitan un nuevo renderizado.

Se usa de la siguiente manera:

```JSX
export const Component() => {
	const ref = useRef();
	const focusInput = () => {
		ref.current.focus();
	}

	return (
		<>
			<input
			type="text"
			ref={ref}
			/>
			<button onCLick={focusInput}>Focus!</button>
		</>
	);
}
```