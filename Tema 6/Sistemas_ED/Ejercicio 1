package Sistemas_ED;

import java.util.function.Function;

public class S1 {
    public static double[][] resolver(Function<Double[], Double[]>[] derivadas, 
                                    double[] y0, double t0, double tf, double h) {
        int n = y0.length;
        int pasos = (int) ((tf - t0) / h);
        double[][] solucion = new double[pasos + 1][n];
        solucion[0] = y0.clone();

        for (int i = 1; i <= pasos; i++) {
            Double[] yActual = new Double[n];
            for (int k = 0; k < n; k++) yActual[k] = solucion[i-1][k];
            
            for (int j = 0; j < n; j++) {
                solucion[i][j] = solucion[i-1][j] + h * derivadas[j].apply(yActual)[j];
            }
        }
        return solucion;
    }

    public static void main(String[] args) {
        // Ejemplo: Oscilador armónico
        @SuppressWarnings("unchecked")
        Function<Double[], Double[]>[] derivadas = new Function[2];
        derivadas[0] = y -> new Double[]{y[1]};     // dy1/dt = y2
        derivadas[1] = y -> new Double[]{-y[0]};    // dy2/dt = -y1

        double[] y0 = {1.0, 0.0};
        double[][] solucion = resolver(derivadas, y0, 0.0, 10.0, 0.01);
        
        System.out.printf("Solución final: y1=%.4f, y2=%.4f%n", 
            solucion[solucion.length-1][0], solucion[solucion.length-1][1]);
    }
}