## Uso
1. Clona el repositorio.
2. Ejecuta el archivo principal:
   ```bash
    import java.util.Scanner;

    public class UNO {

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
