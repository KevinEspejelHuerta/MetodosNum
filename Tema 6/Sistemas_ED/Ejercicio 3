package Sistemas_ED;

public class S3 {
    public interface DerivadaSEDO {
        double[] calcular(double[] y);
    }

    public static double[][] resolver(DerivadaSEDO[] derivadas, 
                                    double[] y0, double t0, double tf, double h) {
        int n = y0.length;
        int pasos = (int) ((tf - t0) / h);
        double[][] solucion = new double[pasos + 1][n];
        solucion[0] = y0.clone();

        for (int i = 1; i <= pasos; i++) {
            // Paso predictor (Euler)
            double[] yPred = new double[n];
            double[] k1 = new double[n];
            for (int j = 0; j < n; j++) {
                k1[j] = derivadas[j].calcular(solucion[i-1])[j];
                yPred[j] = solucion[i-1][j] + h * k1[j];
            }

            // Paso corrector (Heun)
            double[] k2 = new double[n];
            for (int j = 0; j < n; j++) {
                k2[j] = derivadas[j].calcular(yPred)[j];
                solucion[i][j] = solucion[i-1][j] + 0.5 * h * (k1[j] + k2[j]);
            }
        }
        return solucion;
    }

    public static void main(String[] args) {
        // Sistema: Presa-Depredador (Lotka-Volterra simplificado)
        DerivadaSEDO[] derivadas = new DerivadaSEDO[2];
        derivadas[0] = y -> new double[]{0.1 * y[0] - 0.02 * y[0] * y[1]};  // Presas
        derivadas[1] = y -> new double[]{-0.1 * y[1] + 0.01 * y[0] * y[1]}; // Depredadores

        double[] y0 = {40.0, 9.0};
        double[][] solucion = resolver(derivadas, y0, 0.0, 50.0, 0.1);

        System.out.printf("Poblaciones finales: Presas=%.2f, Depredadores=%.2f%n",
            solucion[solucion.length-1][0], solucion[solucion.length-1][1]);
    }
}