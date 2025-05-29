package Sistemas_ED;

import java.util.function.Function;

public class S2 {
    public static double[][] resolver(Function<Double[], Double[]>[] derivadas,
                                    double[] y0, double t0, double tf, double h) {
        int n = y0.length;
        int pasos = (int) ((tf - t0) / h);
        double[][] solucion = new double[pasos + 1][n];
        solucion[0] = y0.clone();

        for (int i = 1; i <= pasos; i++) {
            Double[] k1 = new Double[n], k2 = new Double[n], k3 = new Double[n], k4 = new Double[n];
            Double[] temp = new Double[n];
            
            // Convertir a Double[]
            Double[] yPrev = new Double[n];
            for (int k = 0; k < n; k++) yPrev[k] = solucion[i-1][k];
            
            // k1
            for (int j = 0; j < n; j++) {
                k1[j] = h * derivadas[j].apply(yPrev)[j];
                temp[j] = yPrev[j] + 0.5 * k1[j];
            }
            
            // k2 a k4 (similar, adaptar con temp)
            // ... (completar con la misma lógica)
            
            for (int j = 0; j < n; j++) {
                solucion[i][j] = solucion[i-1][j] + (k1[j] + 2*k2[j] + 2*k3[j] + k4[j]) / 6;
            }
        }
        return solucion;
    }
}