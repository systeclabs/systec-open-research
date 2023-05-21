
## PropTypes

Conforme un componente crece de tamaño, se puede caer en errores al momento de usarlo. Puede que entre sus props, necesite algún atributo que sea *string* y se pase uno de tipo *number*, o que algún prop requerido sea omitido al punto de usarlo. Esto claramente conduce a errores durante el desarrollo.

Una manera de solucionarlos es con TypeScript, sin embargo, React proporciona habilidades de verificación.

Imaginemos que tenemos un componente que recibe un número y lo muestra en pantalla, y al hacer click en un botón, su valor se duplica

```JSX

import { useState } from 'React';


export const Component = ({ number }) => {
	const [state, setState] = useState(number);
	
	const doubleValue = () => {
		setState(state + state);
	}

	return (
		<div>
			<p>Current value: {state} </p>
			<button onClick={doubleValue}>Double it!</button>
		</div>
	);
}
```

  

Ahora supongamos que nuestro componente es utilizado de la siguiente forma:
  

```JSX

<Component number="1" />

```

  Esto causaría un efecto inesperado, y es que, cada vez que el botón sea presionado, nuestro estado será concatenado a sí mismo, causando que sus valores sean

  
Número de Vuelta | Valor del Estado
```
| :---: | :---: |

1 | "1"

2 | "11"

3 | "1111"

4 | "11111111"

5 | "1111111111111111"
```
  

¡Y podría ser peor! ¿Y si nos mandaran una función? ¿O un objeto? Nuestra aplicación se rompería.

Para esto podemos usar los PropTypes y especificar desde un inicio qué tipo de valor está esperando nuestro componente de la siguiente forma:


```JSX
import PropTypes from 'prop-types';
import { useState } from 'React';

export const Component = ({ number }) => {
	const [state, setState] = useState(number);
	const doubleValue = () => {
		setState(state + state);
	}

	return (
		<div>
			<p>Current value: {state} </p>
			<button onClick={doubleValue}>Double it!</button>
		</div>
	);
}

Component.propTypes = {
	number: PropTypes.number.isRequired
}
```

  

Con esto especificamos que forzosamente necesitamos que el prop **number** sea de tipo number.

Los PropTypes no son sólo para verificar números, también podemos comprobar: arreglos, booleanos, funciones, objectos string y symbols.
  
En este [enlace](https://es.reactjs.org/docs/typechecking-with-proptypes.html) podrás revisar el alcance que tienen los PropTypes para tipar nuestros componentes.


## Reglas

## Construir tu propio hook

Todo el código que nosotros escribamos en React debe ser: entendible, escalable y reutilizable. Es por esto que debemos intentar que nuestros componentes sean simples y claros de leer. Y aquí es donde entran los *custom hook*.

Un custom hook es una función común y corriente de JavaScript en la cual se extrae la lógica de un componente con la finalidad de hacerlo reutilizable.

Por estándar, los hooks comienzan con la palabra *use* seguido de un alias a las operaciones que se realizan en él. Por ejemplo, un custom hook que haga peticiones a un servidor, podría llamarse *useFetch*.

Tomemos el custom hook *useFetch* de ejemplo, supongamos que tenemos un componente que hace una petición a una api y muestra la información en pantalla; este componente puede lucir de esta forma:

```JSX
export const Component = () => {

	const [state, setState] = useState();

	useEffect(() => {
		const fetchData = () => {
			const resp = // We fetch data
			setState(resp);
		}
	}, []);

	return (
		<div>Respose: {state}</div>
	);
}
```

Podemos extraer la lógica en nuestro custom hook, el cual luciría de esta manera:

```JSX
// useFetch.js
export const useFetch() {
	const [state, setState] = useState();
	useEffect(() => {
		const fetchData = () => {
			const resp = // We fetch data
			setState(resp);
		}
	}, []);

	return { state };
}
```

Y nuestro el código de nuestro componente sería mucho más fácil de leer

```JSX
// Component.js
export const Component = () => {
	const {state} = useFetch();
	return (
		<div>Respose: {state}</div>
	);
}
```

Este es un ejemplo bastante básico, sin embargo, nuestros componentes pueden retornar tantas funciones o valores como necesitemos y lo mejor, ¡Podemos usarlos en otros componentes!