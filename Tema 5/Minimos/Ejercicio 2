import org.apache.commons.math3.stat.regression.OLSMultipleLinearRegression;

public class M2 {
    public static double[] regresionMultivariable(double[][] x, double[] y) {
        OLSMultipleLinearRegression regression = new OLSMultipleLinearRegression();
        regression.newSampleData(y, x);
        return regression.estimateRegressionParameters();
    }

    public static void main(String[] args) {
        // Datos: y = b0 + b1*x1 + b2*x2
        double[][] x = {{1, 2}, {2, 3}, {3, 4}, {4, 5}, {5, 6}}; // x1 y x2
        double[] y = {3, 5, 7, 9, 11}; // Variable dependiente
        
        double[] coeficientes = regresionMultivariable(x, y);
        System.out.printf("Ecuación: y = %.2f + %.2fx₁ + %.2fx₂\n",
            coeficientes[0], coeficientes[1], coeficientes[2]);
        // Ejemplo: y = 1.00 + 1.00x₁ + 1.00x₂
    }
}