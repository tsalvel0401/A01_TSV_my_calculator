# `1️⃣` A01_TSV_my_calculator + `2️⃣` A02_TSV_my_calculator

### Información:

### Fecha: 16/02/2026 - 19/02/2026
### Nombre: Tonny
### Curso y Grupo: 1º DAW
### Relación UD 3, Actividad 1 + Actividad 2

#### Paso 1: Creación de repositorio remoto
El primer paso a seguir es crear una cuenta en Github, si no se tiene. A continuación, creamos un nuevo repositorio público vacío con el nombre "my_calculator".

#### Paso 2: Creación de repositorio local
En un terminal de nuestro ordenador iniciamos un repositorio local de git. Si se tiene el sistema operativo Windows, se recomienda emplear [Git Bash](https://gitforwindows.org/) como terminal.
```
$ git init my_calculator
$ cd my_calculator
```
y le asignamos el repositorio remoto que acabamos de crear
```
$ git remote add origin git@github.com:<mi usuario de github>/my_calculator.git
```

Por ejemplo, si tu usuario es `pepe`, el comando sería:
```
$ git remote add origin git@github.com:pepe/my_calculator.git
```

#### Paso 3: Añadir ficheros al repositorio

Añadir al directorio de trabajo un fichero con el nombre "index.html". Este fichero contendrá una calculadora web con un botón para calcular el cubo del número introducido:
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Calculator</title>
		<meta charset="utf-8">
	</head>
	<body>
		<h1>Calculadora de Tonny Salvatierra Velázquez</h1>
		Number:
		<input type="text" id="n1">
		<p>
			<button onclick="cube()"> x^3 </button>
		</p>
		<script type="text/javascript">
			function cube() {
				var num = document.getElementById("n1");
				num.value = Math.pow(num.value, 3);
			}
		</script>
	</body>
</html>
```
En la etiqueta h1 debes modificar el texto para incluir tu nombre y apellidos

#### Paso 4: Registrar cambios
A continuación, hay que registrar los ficheros en el índice y crear el primer commit en la rama main. Se recuerda que antes de crear un commit hay que probar siempre que el programa que se va a guardar funciona correctamente (en este caso, abriéndolo en el navegador web y probando que funciona la calculadora).

```
$ git add index.html # Añadir el fichero creado
$ git commit -m "x^3 button" # Congelar los cambios en un commit
$ git log --oneline # Ver la lista de commits
```

#### Paso 5: Crear un segundo commit
Debe crear un segundo commit en la rama en la que está trabajando (main). 
El commit debe añadir a la calculadora (fichero index.html) un segundo botón (elemento HTML `<button ..>`) que eleve un número a la cuarta potencia (x^4) invocando una función (power_4 ()) que calcula x^4 al hacer click en él.

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Calculator</title>
		<meta charset="utf-8">
	</head>
	<body>
		<h1>Calculadora de Tonny Salvatierra Velázquez</h1>
		Number:
		<input type="text" id="n1">
		<p>
			<button onclick="cube()"> x^3 </button>
			<button onclick="power_4()"> x^4</button>
		</p>
		<script type="text/javascript">
			function cube() {
				var num = document.getElementById("n1");
				num.value = Math.pow(num.value, 3);
			}
			function power_4() {
				var num = document.getElementById("n1");
				num.value = Math.pow(num.value, 4);
			}
		</script>
	</body>
</html>
```

Una vez añadido el código del nuevo nuevo botón a la calculadora y después de probar que funciona correctamente, registrar los cambios en el índice y crear el nuevo commit.

```
$ git add index.html
$ git commit -m "x^4 button"
```

#### Paso 6: Subir el repositorio a Github

Para finalizar, hay que subir el repositorio local al repositorio remoto creado en Github inicialmente.

```
$ git push origin main
```

### Entrega
* Añade la URL del repositorio a la tarea. 
* Recuerda que el repositorio tiene que ser publico.
* El nombre del repositorio sera: ID_XXXX_my_calculator donde 
  - ID es el identificador de la tarea
  - XXXX tus iniciales

# `1️⃣` A02_TSV_my_calculator.

### Información:

### Fecha: 19/02/2026
### Nombre: Tonny
### Curso y Grupo: 1º DAW
### Relación UD 3, Actividad 2

#### Paso 7: Crear nueva rama

Imaginemos que un miembro de nuestro equipo comenzase el desarrollo de una nueva funcionalidad partiendo de la versión inicial (sin el botón x^4). Para ello, creamos una rama de nombre "sine" que salga del primer commit (con mensaje "x^3 button") y nos movemos a la rama "sine" en el directorio de trabajo, para poder trabajar sobre ella. Primero tenemos que averiguar cual es el id del commit de nombre "x^3 button" y después crear la rama nueva a partir de él.

```
$ git log --oneline                  # Ver la lista de commits (incluye <commit_id>, p.e. 71e69ce)
$ git checkout -b sine <commit_id>   # Crea rama en commit y realiza checkout a rama
```

#### Paso 8: Crear nuevo commit


Crear un nuevo commit en la rama sine que añada un segundo botón sin(x) a la calculadora en el fichero index.html (además del botón x^3 que ya existe). El nuevo botón debe calcular el seno de un número utilizando la función JavaScript:  Math.sin(x).

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Calculator</title>
		<meta charset="utf-8">
	</head>
	<body>
		<h1>Calculadora de ……su nombre y apellidos……</h1>
		Number:
		<input type="text" id="n1">
		<p>
			<button onclick="cube()"> x^3 </button>
			<button onclick="sine()"> sin </button>
		</p>
		<script type="text/javascript">
			function cube() {
				var num = document.getElementById("n1");
				num.value = Math.pow(num.value, 3);
			}
			function sine() {
				var num = document.getElementById("n1");
				num.value = Math.sin(num.value);
			}
		</script>
	</body>
</html>
```

Estando en la rama sine, se añade el código del nuevo nuevo botón a la calculadora y una vez comprobado que funciona correctamente, registrar los cambios en el índice y crear el nuevo commit con el nombre "sin(x) button".

```
$ git add index.html
$ git commit -m "sin(x) button"
```


#### Paso 9: Integrar la rama "main" en "sine"

Ahora se debe integrar la rama "main" en la rama "sine", para crear una calculadora con tres botones: x^3, x^4 y sin(x).

```
$ git merge main
```

La integración tiene conflictos, que se deben resolver con el editor. Una vez resueltos y después de comprobar que el programa integrado funciona correctamente, se debe finalizar la integración (merge) creando el commit de integración.

```
$ git add index.html
$ git merge --continue # o git commit -m "Integrate main"
```

#### Paso 10: Integrar la rama "sine" en "main"


Ahora que la rama "sine" está correcta y contiene todas las funcionalidades, podemos integrar los cambios en la rama principal "main",
Para ello, nos cambiamos a la rama "main"

```
git checkout main
```

y nos traemos los cambios de "sine".

```
git merge sine
```

Si queremos podemos ver la historia de integraciones de todas las ramas:
```
git log --oneline --graph --all
```

#### Paso 11: Subir todas las ramas del repositorio local al nuevo repositorio en GitHub.

Por último, subimos los cambios realizados en ambas ramas a Github

```
git push --all
```

La opción --force o -f permite subir un repositorio incompatible, pero ¡Cuidado borra el existente! Se debe utilizar solo en casos en que no hay otra solución.


Si accedemos al repositorio creado en Github podemos ver que están ambas ramas con el contenido que hemos subido.