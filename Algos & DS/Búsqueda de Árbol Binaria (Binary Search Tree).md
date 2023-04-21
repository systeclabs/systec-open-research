202207131413
Estado: #idea
Tags: #estructuras-de-datos #trees #algoritmos 

# Búsqueda de Árbol Binaria (Binary Search Tree)

## Descripción
Una [[Visualización Árboles (Trees) |árbol]] de búsqueda binaria es cuando la llave (key) del nodo es **mayor** que todos los nodos del sub-árbol izquierdo y es menor **que** todos los nodos del sub-arbol derecho. 

## Elementos claves

## Pasos para buscar un nodo

1. Comparar la llave del nodo actual con el valor de X. Si es igual hemos encontrado la llave. Termina el programa.
2. Si X es menor a la llave del nodo. Buscamos en el nodo del sub-árbol izquierdo. La razón es que sabemos que el árbol derecho no puede contener valores mayores a X.
3. Si X es mayor que la llave del nodo, buscamos en el sub-árbol derecho.
4. Repetimos el proceso hasta que encontramos la llave o llegamos a un nodo hoja. Si llegamos a un nodo hoja y no hemos encontrado el valor, X no existe.

## Pasos para Insertar un nodo

**1. Comparar el valor de la llave del nodo actual con K.**
2. Si el valor de K es menor al valor del nodo actual:
	1. Si el hijo izquiero del nodo actual es NULL, entonces insertamos el valor de K en el nodo actual y regresamos.
	2. En caso de que el valor del hijo izquiero no sea NULL, el hijo se convierte en el nodo actual y repetimos el proceso del **paso 1**.
3. Si el valor de K es mayor al valor del nodo actual:
	1. Si el hijo derecho del nodo actual es NULL, entonces insertamos el valor de K en el nodo actual y regresamos.
	2. En caso de que el valor del hijo derecho no sea NULL, el hijo se convierte en el nodo actual y repetimos el proceso del **paso 1**.


### Pasos para borrar un nodo

## Implementación

```js
function Node(data) {
	this.data = data;
	this.left = null;
	this.right = null;
}

function BST() {
	this._root = null;
}

```

```js
BST.prototype.insert = function(data) {
	var node = new Node(data);

	// If it's the first node
	if (this._root === null) {
		this._root = node;
	}

	var current = this._root;

	while (current) {
		if (data < current.data) {
			if (current.left === null) {
				current.left = node;
				return;
			}
		
		} else if (data > current.data) {
			if (current.right === null) {
				current.right = node;
				return;				
			}
		
		} else {
			// Duplicates are not supported
			return:
		}		
	}
}
```

```js
BST.prototype.contains = function(data) {
	var current = this_root;

	while (current) {
		if (data === current.data) {
			return true;
		}

		if (data < current.data) {
			current = current.left
		} else {
			current = current.right
		}
	}

	return false;
}
```

```js
var bst = new BST();

console.log('Insert into BST: 5');

bst.insert(5);

console.log('BST contains 5? Returns ' + bst.contains(5));

console.log('BST contains 6? Returns ' + bst.contains(6));
```


### Traversals

#### Pre-Order
Node itself, left, right
```js
BST.prototype.preOrder = function() {
	var output = [];

	function preOrderImpl(node) {
		if (node === null) {
			return;
		}
		// Visit the node itself
		output.push(node.data)

	
		// Visit left sub-tree
		preOrderImpl(node.left);
		
		// Visit the right sub-tree
		preOrderImpl(node.right)
	}

	// Call the internal function
	// with Root as the starting point
	preOrderImpl(this._root);

	return output;


}
```

#### In-Order 
Left sub-tree, node itself, right sub-tree

```js
BST.prototype.inOrder = function() {
	var output = [];

	function preOrderImpl(node) {
		if (node === null) {
			return;
		}
		// Visit left sub-tree
		preOrderImpl(node.left);
		
		// Visit the node itself
		output.push(node.data)
		
		
		// Visit the right sub-tree
		preOrderImpl(node.right)
	}

	// Call the internal function
	// with Root as the starting point
	preOrderImpl(this._root);

	return output;


}
```


#### Pre Order
Left tree, right tree and node itself

```js
BST.prototype.postOrder = function() {
	var output = [];

	function preOrderImpl(node) {
		if (node === null) {
			return;
		}
		// Visit left sub-tree
		preOrderImpl(node.left);
		
		// Visit the right sub-tree
		preOrderImpl(node.right)
		
		// Visit the node itself
		output.push(node.data)
		
	}

	// Call the internal function
	// with Root as the starting point
	preOrderImpl(this._root);

	return output;


}
```

### Execute

```js
var data = [50, 40, 70, 60, 20, 99, 45];
var bst = new BST();

  
for (var i = 0; i < data.length; i++) {
	bst.insert(data[i]);
}

  

console.log("Pre-Order = " + bst.preOrder());
console.log("In-Order = " + bst.inOrder());
console.log("Post-Order = " + bst.postOrder());
```

## Complejidad de Tiempo

## Complejidad de Espacio

---
## Referencias