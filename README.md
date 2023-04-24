```pseudocode
def mcm(n1:int,n2:int, r1:int , r2:int)->int:
    n=2 
    while(n1>1):
        r1= n1%n==0
        print(r1)
        n+=1
        if r1>n1
        break
    while (n2>1):
        r2= n2%n==0
        print(r2)
        n+=1
        if r2>n2
        break

if __name__ == "__main__":
  n1 = int(input("Ingrese numero: "))
  n2 = int(input("Ingrese numero: "))
  factorialDeNum = mcm(n1,n2)
  print( str(factorialDeNum))
  ```
```pseudocode
def Matriz(mat1, mat2):
 for i1 in range(len(mat1)): print(mat1[i1])
 for i2 in range(len(mat2)): print(mat2[i2])    

    

  
if __name__ == "__main__":
  nFilas1 = int(input("Ingrese filas en primera lista: "))
  nCols1 = int(input("Ingrese columnas es primera lista: "))
  nFilas2 = int(input("Ingrese filas en segunda lista: "))
  nCols2 = int(input("Ingrese columnas en segunda lista: "))
  mat1=[]
  fila1=[]
  for i1 in range(nFilas1):
    for j1 in range(nCols1):
     num1=int(input("ingrese elemento de la primera matriz("+str(i1+1)+","+str(j1+1)+"):"))
     fila1.append(num1)
  mat1.append(num1)
  mat2=[]
  fila2=[]
  for i2 in range(nFilas2):
    for j2 in range(nCols2):
      num2=int(input("ingrese elemento de la primera matriz("+str(i2+1)+","+str(j2+1)+"):"))
      fila2.append(num2)
  mat2.append(num2)
  mat2=[]
  fila2=[]
  Matriz(mat1,mat2)
  ```
