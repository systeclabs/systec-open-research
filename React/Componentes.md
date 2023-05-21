## Componentes
En palabras simples, un componente es una parte de tu aplicación independiente y reutilizable.

  
### **¿Por qué usar componentes?**

Imaginemos una página web muy básica, en la que tienes una barra de navegación, esta contiene un menu que lleva a los usuarios a navegar por todo tu sitio web (Inicio, Sobre nosotros, Contacto, etc.). Inicias escribiendo tu código para la página de Inicio, escribes un encabezado, todo el contenido para darle la bienvenida al usuario y un pié de página para darle información adicional al visitante, una vez terminas vas con otra sección de tu sitio, copias y pegas el código del encabezado y del pié de página, escribes toda la información sobre tí o tu negocio y así repites para todas tus demás páginas, y sin duda, esto te funcionará perfectamente.

Pero... eso de estar copiando y pegando codigo repetido no es algo que se le da muy bien a un buen desarrollador, es más, imagina que tienes que hacer un cambio en el encabezado de todas tus secciones, te tomaría tiempo y trabajo que puedes usar para avanzar en otras partes importantes de tu código, pero que si te dijera que puedes escribir o modificar tu codigo una sola vez y afectar a todas tus demás páginas? , y aquí es donde vienen al rescate los componentes de React, que no es más que un trozo de código (por ejemplo puede ser tu encabezado o tu píe de página) que se encarga de evitar tu código repetido, hacer una única función y hacerla muy bien.

En React existen dos tipos de componentes:
  
- Componentes de clase.
- Componentes funcionales.

En esta guía nos centraremos en los **componentes funcionales** ya que son los más nuevos propuestos por React.

### **Componentes funcionales:**
Un componente funcional como lo dice su nombre **Es una función en Javascript** y luce de la siguiente manera:


### **Funcion normal**

```JS
function Welcome(props) {
	return <h1>Hello, {props.name}</h1>;
}

export default Welcome
```

  
### **Funcion de flecha**

```JS
const Welcome = (props) => {
	return <h1>Hello, {props.name}</h1>;
}

export default Welcome
```

Hay algo **importante** que debes notar en este componente, y es que su nombre debe de iniciar con mayuscula para que React lo reconozca como componente, además es importante exportalo para poder usarlo en otro componente.

También notarás que nuestro componente esta recibiendo **props** como parametro, y los **props** no son más que variables que otro componente nos esta enviando, pero esto lo veremos más a fondo en un próximo capitulo.


### **Llamar a un componente desde otro**

Ahora que ya tienes tu componente creado, ya puedes utilizarlo desde otro componente llamandolo de la siguiente manera:


```JS
import Welcome from '/components/Welcome'

<Welcome />

```

> `/components/Welcome` es la ruta en donde se encuentra tu componente creado*/
  
Listo de esa forma ya puedes usar tu componente Welcome en donde quieras, y lo mejor de todo es que si haces un cambio en el componente se verá reflejado en todos los lugares en donde lo estes usando. 

Recuerda que un componente no tiene porque ser tan simple como el ejemplo, puedes agregar toda la lógica que necesites dentro de el, al igual que todo el contenido en JSX que desees.

  

## Ciclo de vida de componentes

Un componente puede pasar por diversas etapas a lo largo de su existencia. Estas etapas se dividen en tres, que corresponden al momento en el que el componente es: montado, actualizado y desmontado.

En versiones anteriores e React, estos tres ciclos se podían encontrar con las siguientes funciones:

```JSX
componentDidMount();
componentDidUpdate();
componentWillUnmount();
```


**componentDidMount()** Es usado para hacer operaciones cuando el componente es montado o creado. Y permite llevar a cabo efectos secundarios cuando el componente se monta (Una petición a un servidor, por ejemplo)

**componentDidUpdate(prevProps)** Se ejecuta cada vez que cambia el estado dentro de nuestra aplicación, también permite ejecutar operaciones con efectos secundarios.

**componentWillUnmount();** Se llamará cada vez que el componente vaya a ser desmontado, es de mucha utilidad para hacer limpieza. Un caso muy útil es cuando un componente que utiliza algún `eventListener` es creado y eliminado varias veces. No queremos tener múltiples `evetListener` haciendo lo mismo o peor, cosas que ya no necesitamos. También es muy útil para cancelar operaciones asíncronas. !Evita las fugas de memoria!

Los tres métodos mencionados anteriormente son para Class Componentes o componentes basados en clases. Pero, a partir de la versión 16.8 de React, contamos con los hooks, los cuales nos permiten controlar el estado de la aplicación de forma más sencilla.

Entre los hooks disponibles, el que cubre los tres métodos anteriormente es el hook de efecto `useEffect`

**Montado**

```JSX

useEffect(() => {

	console.log('This will be executed when the component is created. What about calling our server?');
	
	return () => {
	
	console.log('This will be executed when your component is destroyed. What about cancelling asynchronous operations?');

}

}, [dependencyArray]); // Will re execute your effect every time a variable of your dependency array change

```

  
Más adelante, iremos a fondo sobre este hook. Hay cosas que debemos evitar o seguir para mantener las buenas prácticas.