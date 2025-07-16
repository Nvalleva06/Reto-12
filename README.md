# Reto-12
1. Desarrollar un algoritmo que imprima de manera ascendente los valores (todos del mismo tipo) de un diccionario.
2. Desarrollar una función que reciba dos diccionarios como parámetros y los mezcle, es decir, que se construya un nuevo diccionario con las llaves de los dos diccionarios; si hay una clave repetida en ambos diccionarios, se debe asignar el valor que tenga la clave en el primer diccionario.
3. Dado el JSON:
4. A través de un programa conectese a al menos 3 [API's ](https://apipheny.io/free-api/), obtenga el JSON, imprimalo y extraiga los pares de llave : valor.
```JSON
{
	"jadiazcoronado":{
		"nombres": "Juan Antonio",
		"apellidos": "Diaz Coronado",
		"edad":19,
		"colombiano":true,
		"deportes":["Futbol","Ajedrez","Gimnasia"]
	},
	"dmlunasol":{
		"nombres": "Dorotea Maritza",
		"apellidos": "Luna Sol",
		"edad":25,
		"colombiano":false,
		"deportes":["Baloncesto","Ajedrez","Gimnasia"]
	}
}
```
 Cree un programa que lea de un archivo con dicho JSON y: 
 - Imprima los nombres completos (nombre y apellidos) de las personas que practican el deporte ingresado por el usuario.
 - Imprima los nombres completos (nombre y apellidos) de las personas que estén en un rango de edades dado por el usuario.

4. A través de un programa conectese a al menos 3 [API's ](https://apipheny.io/free-api/), obtenga el JSON, imprimalo y extraiga los pares de llave : valor.

## 1. Desarrollar un algoritmo que imprima de manera ascendente los valores (todos del mismo tipo) de un diccionario.
```python
# Creamos un diccionario con letras y valores asignados
letras_valores = {
    'a': 42, 'b': 15, 'c': 33, 'd': 8,  'e': 56, 'f': 21, 'g': 4,
    'h': 78, 'i': 12, 'j': 29, 'k': 65, 'l': 3,  'm': 37, 'n': 19,
    'o': 50, 'p': 6,  'q': 44, 'r': 9,  's': 71, 'u': 18, 'v': 31,
    'w': 23, 'x': 39, 'y': 1,  'z': 60
}

# Extraemos todos los valores del diccionario usando .values() y los convertimos a una lista
valores = list(letras_valores.values())

# Ordenamos los valores de menor a mayor usando .sort()
valores.sort()

# Mostramos los valores ya ordenados
print("Valores en orden ascendente:")
for valor in valores:
    print(valor, end=" ")
```
## 2. Desarrollar una función que reciba dos diccionarios como parámetros y los mezcle, es decir, que se construya un nuevo diccionario con las llaves de los dos diccionarios; si hay una clave repetida en ambos diccionarios, se debe asignar el valor que tenga la clave en el primer diccionario.
```python
from pprint import pprint

# Definimos una función que recibe dos diccionarios y devuelve uno nuevo mezclado
def mezclar_diccionarios(dic1, dic2):
    # Hacemos una copia del primer diccionario para no modificar el original
    mezclado = dic1.copy()

    # Recorremos el segundo diccionario y agregamos sus elementos solo si la clave no está en el primero
    for clave, valor in dic2.items():
        if clave not in mezclado:
            mezclado[clave] = valor

    # Retornamos el nuevo diccionario con las claves combinadas
    return mezclado

# Creamos dos diccionarios de ejemplo con algunas claves repetidas
diccionario1 = {
    "manzana": "fruta",
    "perro": "animal",
    "cielo": "azul",
    "fuego": "calor",
    "lluvia": "agua",
    "roca": "dura",
    "flor": "olor",
    "tren": "veloz",
    "mar": "salado",
    "nube": "algodón",
    "pájaro": "vuelo",
    "sol": "luz",
    "tierra": "suelo",
    "viento": "aire",
    "montaña": "alta",
    "río": "corriente",
    "noche": "oscura",
    "arena": "playa",
    "hoja": "verde",
    "lago": "tranquilo"
}

diccionario2 = {
    "pelota": "juego",
    "perro": "animal",
    "lago": "tranquilo",
    "ventana": "vidrio",
    "puerta": "entrada",
    "camino": "andar",
    "fuego": "calor",
    "estrella": "brilla",
    "ratón": "pequeño",
    "mesa": "madera",
    "libro": "leer",
    "computador": "tecnología",
    "silla": "sentarse",
    "planta": "vida",
    "auto": "rápido",
    "avión": "cielo",
    "mariposa": "colores",
    "sol": "luz",
    "carro": "motor",
    "puente": "cruzar"
}

# Usamos la función para combinar ambos diccionarios, priorizando los valores del primero
resultado = mezclar_diccionarios(diccionario1, diccionario2)

# Imprimimos el diccionario resultante en orden alfabético por clave
print("Diccionario mezclado (ordenado alfabéticamente):")
for clave in sorted(resultado):
    print(f"{clave} : {resultado[clave]}")

# También mostramos todo el diccionario en una sola línea usando pprint
print("\nDiccionario mezclado (en una sola línea):")
pprint(resultado)
```

## 3. Dado el JSON:
```python
import json

# Cargamos el JSON directamente como texto multilínea
datos_json = '''
{
    "jadiazcoronado":{
        "nombres": "Juan Antonio",
        "apellidos": "Diaz Coronado",
        "edad":19,
        "colombiano":true,
        "deportes":["Futbol","Ajedrez","Gimnasia"]
    },
    "dmlunasol":{
        "nombres": "Dorotea Maritza",
        "apellidos": "Luna Sol",
        "edad":25,
        "colombiano":false,
        "deportes":["Baloncesto","Ajedrez","Gimnasia"]
    }
}
'''

# Convertimos el texto en un diccionario usando json.loads
personas = json.loads(datos_json)

# Pedimos al usuario un deporte y buscamos quién lo practica
deporte = input("Ingrese el deporte que desea buscar: ").lower()

print("\nPersonas que practican ese deporte:")
for clave in personas:
    persona = personas[clave]
    for d in persona["deportes"]:
        if d.lower() == deporte:
            nombre_completo = persona["nombres"] + " " + persona["apellidos"]
            print("-", nombre_completo)

# Ahora pedimos el rango de edades
edad_min = int(input("\nIngrese la edad mínima: "))
edad_max = int(input("Ingrese la edad máxima: "))

print(f"\nPersonas entre {edad_min} y {edad_max} años:")
for clave in personas:
    persona = personas[clave]
    edad = persona["edad"]
    if edad_min <= edad <= edad_max:
        nombre_completo = persona["nombres"] + " " + persona["apellidos"]
        print("-", nombre_completo)
```
## 4 A través de un programa conectese a al menos 3 [API's ](https://apipheny.io/free-api/), obtenga el JSON, imprimalo y extraiga los pares de llave : valor.
```python
import requests

# Nos conectamos a tres APIs distintas, obtenemos el JSON, lo imprimimos y mostramos sus pares clave:valor

# API 1: API de chistes de Chuck Norris
url1 = "https://api.chucknorris.io/jokes/random"
respuesta1 = requests.get(url1)
datos1 = respuesta1.json()
print("\n--- API 1: Chiste de Chuck Norris ---")
print(datos1)

print("\nLlaves y valores:")
for clave, valor in datos1.items():
    print(f"{clave}: {valor}")

# API 2: API de actividad aleatoria (Bored API)
url2 = "https://www.boredapi.com/api/activity"
respuesta2 = requests.get(url2)
datos2 = respuesta2.json()
print("\n--- API 2: Actividad aleatoria ---")
print(datos2)

print("\nLlaves y valores:")
for clave, valor in datos2.items():
    print(f"{clave}: {valor}")

# API 3: API de persona aleatoria
url3 = "https://randomuser.me/api/"
respuesta3 = requests.get(url3)
datos3 = respuesta3.json()
print("\n--- API 3: Persona aleatoria ---")
print(datos3)

print("\nLlaves y valores del primer resultado:")
for clave, valor in datos3["results"][0].items():
    print(f"{clave}: {valor}")
```
