# Desarrollar un algoritmo que imprima de manera ascendente los valores (todos del mismo tipo) de un diccionario.
```pseudocode
def ValoresAscendente(diccionario):  #define la funcion

    valores = sorted(diccionario.values()) #ordena los valores de forma ascendente

    for valor in valores: #Se itera sobre la lista de valores

        print(valor) #imprime cada valor
  ```
  # 2.Desarrollar una funci�on que reciba dos diccionarios como par�ametros y los mezcle, es decir, que se construya un nuevo diccionario con las llaves de los dos diccionarios; si hay una clave repetida en ambos diccionarios, se debe asignar el valor que tenga la clave en el primer diccionario. 
```pseudocode
def mezclar_diccionarios(x, y): # define la funcion

    Mix = dict(y)  # Crea una copia del segundo diccionario

    for clave, valor in a.items(): #itera sobre las claves y valores del primer diccionario

        if clave not in Mix: 

            Mix[clave] = valor

    return Mix

diccionario1 = {'x': 10, 'b': 20, 'c': 30, 'd': 40}

diccionario2 = {'y': 20, 'd': 70, 'e': 50, 'f': 40}

diccionarioTeclado = mezclarDiccionarios(diccionario1, diccionario2)

print(diccionarioTeclado)
```
# 3.Cree un programa que lea de un archivo con dicho JSON y:
-Imprima los nombres completos (nombre y apellidos) de las personas que practican el deporte ingresado por el usuario.
-Imprima los nombres completos (nombre y apellidos) de las personas que est�en en un rango de edades dado por el usuario.
```pseudocode 

import json

def Json(archivo):
    with open(archivo, 'r') as file:
        data = json.load(file)
    return data
def NombresDeporte(data, deporte):
    for usuario, info in data.items():
        if deporte in info['deportes']:
            nombres = info['nombres']
            apellidos = info['apellidos']
            nombreCompleto = f"{nombres} {apellidos}"
            print(nombreCompleto)
def NombresRangoEdades(data, edadMin, edadMax):
    for usuario, info in data.items():
        edad = info['edad']
        if edadMin <= edad <= edadMax:
            nombres = info['nombres']
            apellidos = info['apellidos']
            nombreCompleto = f"{nombres} {apellidos}"
            print(nombreCompleto)

ArchivoJson = 'datos.json'
data = Json(archivoJson)

deporteIngresado = input("Ingrese el nombre del deporte : ")
print("Nombres de personas que practican", deporteIngresado)
NombresDeporte(data, deporteIngresado)

edadMinima = int(input("Ingrese la edad mínima: "))
edadMaxima = int(input("Ingrese la edad máxima: "))
print("Nombres de personas en el rango es de ", edadMinima, "a", edadMaxima)
NombresRangoEdades(data, edadMinima, edadMaxima)
```
# 4. Revise los campos: 'alertAlertas', 'alertPrecip', 'alertTmpMax', 'alertTmpMin', 'alertVelViento'. Para cada uno identifique si se presentan alertas ({0: x} indica que el día 0 habra un fenomeno de la alerta en cuestión, {1:"-"} indica que no habrá ningun fenomeno climatico). En caso que se presente una alerta obtenga la fecha del campo 'dt' (aquí pueden revisar como se convierte de UTC a fecha), así como los parametros relevantes del evento (e.g. si es un fenomeno de lluvias, busqye el nivel de lluvia, si es vientos, la velocidad del viuento). Al final deberá imprimir las fechas de alerta, el tipo de alerta y las variables asociadas.
```pseudocode
import json
from datetime import datetime
jsonString = '''
{\"dt\": {\"0\": 1685116800, \"1\": 1685203200, \"2\": 1685289600, \"3\": 1685376000, \"4\": 1685462400, \"5\": 1685548800, \"6\": 1685635200, \"7\": 1685721600}, \"sunrise\": {\"0\": 1685097348, \"1\": 1685183745, \"2\": 1685270143, \"3\": 1685356542, \"4\": 1685442942, \"5\": 1685529342, \"6\": 1685615743, \"7\": 1685702145}, \"sunset\": {\"0\": 1685143042, \"1\": 1685229458, \"2\": 1685315875, \"3\": 1685402291, \"4\": 1685488708, \"5\": 1685575124, \"6\": 1685661541, \"7\": 1685747958}, \"moonrise\": {\"0\": 1685118300, \"1\": 1685207460, \"2\": 1685296620, \"3\": 1685385720, \"4\": 1685474880, \"5\": 1685564220, \"6\": 1685653740, \"7\": 1685743500}, \"moonset\": {\"0\": 0, \"1\": 1685164320, \"2\": 1685253000, \"3\": 1685341560, \"4\": 1685430120, \"5\": 1685518740, \"6\": 1685607600, \"7\": 1685696640}, \"moon_phase\": {\"0\": 0.22, \"1\": 0.25, \"2\": 0.28, \"3\": 0.31, \"4\": 0.35, \"5\": 0.38, \"6\": 0.41, \"7\": 0.45}, \"pressure\": {\"0\": 1011, \"1\": 1012, \"2\": 1012, \"3\": 1012, \"4\": 1012, \"5\": 1012, \"6\": 1012, \"7\": 1011}, \"humidity\": {\"0\": 85, \"1\": 61, \"2\": 68, \"3\": 74, \"4\": 84, \"5\": 66, \"6\": 81, \"7\": 82}, \"dew_point\": {\"0\": 23.93, \"1\": 22.5, \"2\": 23.67, \"3\": 23.35, \"4\": 24.22, \"5\": 22.73, \"6\": 22.58, \"7\": 24.02}, \"wind_speed\": {\"0\": 2.94, \"1\": 2.95, \"2\": 2.88, \"3\": 2.76, \"4\": 2.77, \"5\": 2.97, \"6\": 2.94, \"7\": 2.79}, \"wind_deg\": {\"0\": 196, \"1\": 182, \"2\": 182, \"3\": 177, \"4\": 183, \"5\": 193, \"6\": 195, \"7\": 181}, \"weather\": {\"0\": {\"id\": 804, \"main\": \"Clouds\", \"description\": \"overcast clouds\", \"icon\": \"04n\"}, \"1\": {\"id\": 500, \"main\": \"Rain\", \"description\": \"light rain\", \"icon\": \"10d\"}, \"2\": {\"id\": 803, \"main\": \"Clouds\", \"description\": \"broken clouds\", \"icon\": \"04d\"}, \"3\": {\"id\": 803, \"main\": \"Clouds\", \"description\": \"broken clouds\", \"icon\": \"04d\"}, \"4\": {\"id\": 804, \"main\": \"Clouds\", \"description\": \"overcast clouds\", \"icon\": \"04n\"}, \"5\": {\"id\": 803, \"main\": \"Clouds\", \"description\": \"broken clouds\", \"icon\": \"04n\"}, \"6\": {\"id\": 803, \"main\": \"Clouds\", \"description\": \"broken clouds\", \"icon\": \"04n\"}, \"7\": {\"id\": 803, \"main\": \"Clouds\", \"description\": \"broken clouds\", \"icon\": \"04d\"}}, \"clouds\": {\"0\": 100, \"1\": 100, \"2\": 66, \"3\": 64, \"4\": 98, \"5\": 67, \"6\": 83, \"7\": 60}, \"pop\": {\"0\": 0, \"1\": 0.2, \"2\": 0, \"3\": 0, \"4\": 0.4, \"5\": 0, \"6\": 0, \"7\": 0}, \"uvi\": {\"0\": 0, \"1\": 1.36, \"2\": 2.29, \"3\": 1.85, \"4\": 0, \"5\": 1.89, \"6\": 2.24, \"7\": 1.42}}
'''
data = json.loads(jsonString)
numereCord = len(data['dt'])
for x in range(numereCord):
    time = data['dt'][str(i)]
    sunriseTime = data['sunrise'][str(x)]
    sunsetTimesMode = data['sunset'][str(x)]

    date = datetime.fromtime(time)
    sunrise = datetime.fromtime(sunriseTime)
    sunset = datetime.fromtime(sunsetTimesMode)

    print(f"Registro {x+1}")
    print("Fecha y hora:", date)
    print("Amanecer:", sunrise)
    print("Atardecer:", sunset)

```
# 5. A través de un programa conectese a al menos 3 API's , obtenga el JSON, imprimalo y extraiga los pares de llave : valor.
```pseudocode
import json
import requests

url = 'https://api.publicapis.org/entries'

def buscarAPIPorIndice(num: int):
    params = {'title': str(num)}
    peticion = requests.get(url, params=params)
    print(peticion.url)
    print(peticion.status_code)

    data = json.loads(peticion.text)
    if data['count'] > 0:
        api = data['entries'][0]['API']
        return api
    else:
        return None

if _name_ == "_main_":
    num_indice = int(input("Ingrese el número del índice: "))
    respuesta = buscarAPIPorIndice(num_indice)
    if respuesta:
        print("El valor de la clave 'API' es:", respuesta)
    else:
        print("No se encontró ninguna entrada para el índice proporcionado.")

url = 'https://api.agify.io'

def obtenerInformacionPorNombre(nombre: str):
    params = {'name': nombre}
    peticion = requests.get(url, params=params)
    print(peticion.url)
    print(peticion.status_code)

    data = json.loads(peticion.text)
    return data

if _name_ == "_main_":
    nombre = input("Ingrese la llave: ")
    respuesta = obtenerInformacionPorNombre(nombre)
    print("Información para el nombre:", nombre)
    print(json.dumps(respuesta, indent=2))
 
import requests
import json

url = 'https://dog.ceo/api/breeds/image/random'

def obtenerImagenPerro():
    peticion = requests.get(url)
    print(peticion.url)
    print(peticion.status_code)

    data = json.loads(peticion.text)
    imagen = data['message']
    return imagen

if _name_ == "_main_":
    imagen_perro = obtenerImagenPerro()
    print("Imagen aleatoria de perro:")
    print(imagen_perro) 
```
  























