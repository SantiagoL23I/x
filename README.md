```pseudocode
def ValoresAscendente(diccionario):  #define la funcion

    valores = sorted(diccionario.values()) #ordena los valores de forma ascendente

    for valor in valores: #Se itera sobre la lista de valores

        print(valor) #imprime cada valor





    

    

    

    




    
    
        
        
        
       
        

        
        
       
        







  ```
  
```pseudocode


import requests

def obtenerDatos(api_url):

    response = requests.get(api_url)

    jsonData = response.json()

    print("JSON:")

    print(jsonData)

    print()

    print("Pares de llave-valor:")

    for key, value in jsonData.items():

        print(f"Llave: {key}, Valor: {value}")

    print()

print("Genshin Impact")

obtenerDatos("https://api.genshin.dev/")

print("Dolar")

obtenerDatos("https://api.exchangerate-api.com/v4/latest/USD")

print("Tabla periodica")

obtenerDatos("https://neelpatel05.pythonanywhere.com/")
```
```pseudocode
def mezclar_diccionarios(a, b): # define la funcion

    Mix = dict(b)  # Crea una copia del segundo diccionario

    for clave, valor in a.items(): #itera sobre las claves y valores del primer diccionario

        if clave not in Mix: 

            Mix[clave] = valor

    return Mix

diccionario1 = {'a': 10, 'b': 20, 'c': 30, 'd': 40}

diccionario2 = {'b': 20, 'd': 70, 'e': 50, 'f': 40}

diccionarioTeclado = mezclarDiccionarios(diccionario1, diccionario2)

print(diccionarioTeclado)

```
```pseudocode 



```
    

  























