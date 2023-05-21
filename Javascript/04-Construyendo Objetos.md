JavaScript no tiene clases, pero se pueden crear objetos utilizando "function constructors". Una **"function constructor"** es una función normal que se utiliza para construir objetos. La variable **`this`** apunta a un nuevo objeto vacío, y ese objeto se devuelve automáticamente desde la función. En lugar de utilizar la palabra clave **`class`** como en otros lenguajes de programación, en JavaScript se utilizan las "function constructors" para crear objetos y asignarles propiedades y métodos.

```js
function Person(firstname, lastname) {
	console.log(this); // 'this' apunta a un objeto vacio
	// agregando propiedades
	this.firstname = firstname,
	this.lastname = lastname
	
	console.log('This function is invoked');
}
```

Las funciones constructoras integradas (Built-in Function Constructors) en JavaScript son funciones que se utilizan para crear objetos con valores iniciales. Por ejemplo, la función constructora "Number" se utiliza para crear un objeto que contiene un valor numérico.

Algunas de las funciones constructoras integradas en JavaScript son "Number", "String", "Boolean", "Object", "Array", "Function", "RegExp", y "Date". Cada una de estas funciones constructoras se utiliza para crear objetos de un tipo específico, y cada uno de ellos tiene propiedades y métodos propios.

```js
// PROTOTYPE //
Person.prototype.getFullName = function() {
	return this.firstname + ' ' + this.lastname;
} 
// this is more efficient because you create only one copy in memory


// 'new' is Java like (Marketing bull)
// invoking Person generates an Execution Context with 'this' property
var vala = new Person('Vala', 'Licious'); 
console.log(vala);

var kary = new Person('Kary', 'Lups');
console.log(kary);

  

Person.prototype.getFormalFullName = function() {
	return this.lastname + ' ' + this.firstname;
}

  
console.log(vala.getFormalFullName());

```

Por ejemplo, el código define dos objetos llamados "vala" y "kary" que se crean a partir de la función constructora "Person". Estos objetos tienen como propiedades el primer nombre y el apellido.

Luego, se define una nueva propiedad de prototipo para la función constructora "Person" utilizando la sintaxis "Person.prototype". La nueva propiedad se llama "getFormalFullName" y es una función que devuelve el apellido seguido del primer nombre.

Cuando se crean los objetos "vala" y "kary", heredan automáticamente la propiedad de prototipo "getFormalFullName" definida en la función constructora "Person". Esto significa que estos objetos también tienen la función "getFormalFullName" que devuelve el apellido seguido del primer nombre.

Por último, se imprimen los objetos "vala" y "kary" en la consola utilizando "console.log".

>También es importante tener en cuenta que al utilizar las funciones constructoras integradas, se pueden crear objetos con valores iniciales, pero también se pueden extender esas funciones para agregar propiedades y métodos personalizados.


