# 1. Formulación del problema

<p align="center">
  <img src="image.png" alt="Imagen del ejercicio n°1" />
</p>

# 2. Resolución

> I) Entrada del valor de la variable "dimension"
- Al iniciar el algoritmo se incializa la libreria java "Scanner" para ingresar datos de entrada, empezando desde la función `main` .
- Se solicitara al usuario ingresar un valor para la `variable "d"`, dicho dato sera el n° de filas y n° de columnas de la matriz cuadratica.

```bash
 import java.util.Scanner;
```

```bash
    public static void main(String[] args) {
     Scanner sc = new Scanner(System.in);
        System.out.println("Ingresar dimension [d]: ");
        int d = sc.nextInt();
        
        if(d <= 0){
           d = sc.nextInt();;
        }
```
> II) Ingreso de numeros enteros en la matriz 
- Ingresado el dato, se inicializa un array int[] `"almacenar_sumadiagonal"` para guardar las próximas sumatorias en diagonal. Asimismo, se realiza un llamado a la `"función calcular(d)"`, que se encargará de realizar dicho proceso utilizando la `variable "d"`.
```bash
    int[] almacenar_sumadiagonal = calcular(d);
```
- Se inicializa una `Matriz` de tamaño d x d y un array llamado `almacenar_sumadiagonal`, que tendrá capacidad para 2 elementos. Luego, se recorre cada elemento de la matriz con tal de ingresar un valor numerico a cada uno.

```bash     
    public static int[] calcular(int d){
    Scanner sc = new Scanner(System.in);      
    int[] almacenar_sumadiagonal = new int[2];
    int[][] Matriz = new int[d][d];
    
    for(int i=0; i < d; i++){
        for(int j=0; j < d;j++){
            System.out.print("["+i+"]"+"[" + j+"]");
            Matriz[i][j] = sc.nextInt();
        }
    }
```    
> III) Impresión y calculo de la sumas diagonales de la matriz

- Calcular las diagonales de una matriz se refiere que en un recorrido de una matriz cada vez que el index de n° de filas y n° de columnas sean iguales se almacene ese numero en la variable almacenadora,en este caso, el array `"almacenar_sumadiagonal"` tomara el rol de almacenar tales sumatorias,pero como tambien se pide la sumatoria desde la esquina superior derecha, entonces se inicializa una variable `"k"`, que es equivalente al ultimo index de la matriz (d - 1).
- Se vuelve a hacer un recorrido para: imprimir la matriz e comparar si en index el n° de columna es igual al n° de fila,si fuese el caso se almacena el dato. Mientras la variable `"i"` aumenta su valor en 1 cada vez que recorra una fila, la variable `"k"` decrece en 1, esto ocurre para obtener ambas diagonales respectivamente y almacenarlas en sus respectivo elemento de `"almacenar_sumadiagonal"`.

```bash   
    System.out.println("MATRIZ: ");
        
    int k = d - 1;
    for(int i= 0;i < d;i++){
        
        for(int j=0; j < d;j++){
            System.out.print("["+Matriz[i][j]+"]");
            if(j == i){
            almacenar_sumadiagonal[0] += Matriz[i][j];    
            }
            if(j == k){
            almacenar_sumadiagonal[1] += Matriz[i][j];    
            }
            
        }
    System.out.println("");    
    k--;

      
    }
    return almacenar_sumadiagonal;  
    }
```
> IV) Asignación e impresión de salida de los resultados de las sumas diagonales de la matriz dXd

- Finalmente, la función `"calcular"` expulsa el resultado en el array inicializado de la función `"main"` y se imprimen los datos de salida.

```bash   
        int[] almacenar_sumadiagonal = calcular(d);
        System.out.println("SUMA DIAGONAL IZQUIERDA: " + almacenar_sumadiagonal[0]);
        System.out.println("SUMA DIAGONAL DERECHA: " + almacenar_sumadiagonal[1]);
    }
```

### Codigo completo

```bash
import java.util.Scanner;

    public class Main {

    public static int[] calcular(int d){
    Scanner sc = new Scanner(System.in);    
        
    int[] almacenar_sumadiagonal = new int[2];
    int[][] Matriz = new int[d][d];
    
    for(int i=0; i < d; i++){
        for(int j=0; j < d;j++){
            System.out.print("["+i+"]"+"[" + j+"]");
            Matriz[i][j] = sc.nextInt();
        }
    }
    
    System.out.println("MATRIZ: ");
        
    int k = d - 1;
    for(int i= 0;i < d;i++){
        
        for(int j=0; j < d;j++){
            System.out.print("["+Matriz[i][j]+"]");
            if(j == i){
            almacenar_sumadiagonal[0] += Matriz[i][j];    
            }
            if(j == k){
            almacenar_sumadiagonal[1] += Matriz[i][j];    
            }
            
        }
    System.out.println("");    
    k--;

      
    }
    return almacenar_sumadiagonal;  
    }
    
    public static void main(String[] args) {
     Scanner sc = new Scanner(System.in);
        System.out.println("Ingresar dimension [d]: ");
        int d = sc.nextInt();
        
        if(d <= 0){
           d = sc.nextInt();;
        }
        
        int[] almacenar_sumadiagonal = calcular(d);
        System.out.println("SUMA DIAGONAL IZQUIERDA: " + almacenar_sumadiagonal[0]);
        System.out.println("SUMA DIAGONAL DERECHA: " + almacenar_sumadiagonal[1]);
    }
    
}
```
# 3. Complejidad

> I) Entrada del valor de la variable "dimension"

- Complejidad de tiempo: 𝑂(1)  (debido a un número fijo de operaciones, siendo el peor caso que se ingrese un numero para `"d"` que sea <= 0, puede volverse 𝑂(k) ).
- Complejidad de espacio: 𝑂(1) (debido al uso de una cantidad fija de memoria).

> II) Ingreso de numeros enteros en la matriz 

- Complejidad de tiempo: 𝑂(d²) (debido al recorrido en doble bucle)
- Complejidad de espacio: 𝑂(d²) (si bien `"almacenar_sumadiagonal"` ocupa 𝑂(2) por tener 2 elementos, se utiliza una estructura bidimensional en la matriz lo que lo lleva a ser 𝑂(d²) en total)

> III) Impresión y calculo de la sumas diagonales de la matriz

- Complejidad de tiempo: 𝑂(d²) (debido al recorrido en doble bucle)
- Complejidad de espacio: 𝑂(d²) (al ser declarada previamente una matriz dxd, ocupa 𝑂(d²))

> IV) Asignación e impresión de salida de los resultados de las sumas diagonales de la matriz dXd

- Complejidad de tiempo: 𝑂(d²) (debido a que el array `"almacenar_sumadiagonal"` equivale a la función `"calcular(d)"`) 
- Complejidad de espacio: 𝑂(d²) (el espacio está dominado por el uso de la matriz y las operaciones de cálculo dentro de la función  `"calcular(d)"`, al igual que el tiempo)
