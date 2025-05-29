import java.text.DecimalFormat;

public class C2 {
    public static double[][] calcular(double[][] datos) {
        int nVariables = datos.length;
        double[][] matriz = new double[nVariables][nVariables];
        
        for (int i = 0; i < nVariables; i++) {
            for (int j = 0; j < nVariables; j++) {
                matriz[i][j] = CorrelacionPearson.calcular(datos[i], datos[j]);
            }
        }
        return matriz;
    }

    public static void main(String[] args) {
        double[][] variables = {
            {1, 2, 3, 4, 5},    // Variable 1
            {2, 4, 6, 8, 10},    // Variable 2
            {5, 3, 1, -1, -3}    // Variable 3
        };
        
        double[][] matriz = calcular(variables);
        DecimalFormat df = new DecimalFormat("0.000");
        
        System.out.println("Matriz de Correlación:");
        for (double[] fila : matriz) {
            for (double r : fila) {
                System.out.print(df.format(r) + "\t");
            }
            System.out.println();
        }
        /* Salida:
        1.000   1.000   -1.000
        1.000   1.000   -1.000
        -1.000  -1.000  1.000
        */
    }
}