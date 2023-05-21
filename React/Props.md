
### **¿Que son los props?**

Los props no son más que variables que puedes enviar desde un componente padre a un componente hijo.

Estos props pueden contener cualquier tipo:

- Texto
- Numero
- Arreglos
- Booleanos
- Objetos

Veamos un ejemplo de como puede un componente padre puede enviar props a su componente hijo.

  
#### **Componente padre**

```JS
import Hijo from './Hijo'

const Padre = () => {
	return (
	
		<Hijo
		name = "Alexander"
		age = {23}
		favoriteColors = {["Blue", "Green", "Purple"]}
		familyNames = {{
		father: "Mike",
		mother: "Rose",
		sister: "Emily"
		}}
		/>
	)
}

export default Padre
```
  
Veamos a profundidad que esta pasando en el componente padre:

Antes que nada importamos el componente hijo `import Hijo from './Hijo'` al que le enviaremos los props desde el padre, recuerda que **'./Hijo'** es la ruta en donde esta creado el componente.

Si quisieramos usar el componente hijo dentro del componente padre, simplemente lo usaríamos de esta forma: `<Hijo />` pero como nuestra intención en este ejemplo es pasarle props notaremos que tiene algunas cosas adicionales que no son nada más que nombres de variables (name, age, favoriteColors, familyNames) con sus respectivos valores.

Hay algo muy importante en cada props que queremos enviar, y es que, todas estan encerradas entre **{ }** ( menos **name** que contiene un string ) y esto es para decirle a JSX que ese contenido lo debe de interpretar como JavaScript nativo y no como una cadena de texto. te estarás preguntando que pasa con las dobles {} en **familyNames** y la respuesta es simple:

Las llaves externas son las que usará JSX y las segundas es porque estas enviando un objeto de Javascript y un objeto se representa con {}.

Ahora vamos a ver como recibir esas props en el componente hijo:

#### **Componente hijo**

```JS
const Hijo = (props) => {
	console.log(props);
	return (
		<div>
		<h1>Welcome {props.name}</h1>
		</div>
	);
}

export default Hijo
```

Como puedes ver se recibe como parametro **props** que no es más que un objeto con todas las propiedades que esta enviando el componente padre, dejamos `console.log(props)` intencionalmente para que puedas ver lo que trae

#### **Respuesta del console log**

```JS

{
	age: 23
	familyNames:{
	
		father: "Mike"
		
		mother: "Rose"
		
		sister: "Emily"
	
	}
	favoriteColors:[
	
		"Blue"
		
		"Green"
		
		"Purple"
	
	]
	name: "Alexander"
}

```


Y como es solo un objeto de JavaScript puedes acceder a sus propiedades:

`<h1>Hijo to props {props.name}</h1>` o bien puedes usar destructuring de Javascript para ahorrarte un poco de código:


#### **Componente hijo destructuring props**

```JS
const Hijo = ({name, age}) => {
	return (
		<div>
			<h1>Welcome {name}, your age is {age}</h1>
		</div>
	)
}
```


Ahora imaginemos que estamos esperando recibir el valor de **lastname** en las props que serán enviadas por el componente padre y tu app realiza algunas acciones importantes con ese valor, adivina que pasará...? si, tu app volará en mil pedazos, pero tranquilx React y sus props tienen la solución para esto: **Props con valor por defecto** y se usan de esta forma:


```JS
const Hijo = ({name, age, lastname = "Mike"} ) => {
	return (
		<div>
		<h1>Welcome {name} {lastname}, your age is {age}</h1>
		</div>
	);
}
```


Y ahora sí, tu app seguirá funcionando aunque el padre no envie esa props.