import java.text.DecimalFormat;

public class R4 {
    public static double[] calcular(double[] x, double[] y) {
        if (x.length != y.length) throw new IllegalArgumentException("Arrays deben tener igual longitud");
        
        // Transformación logarítmica: ln(y) = ln(a) + b*ln(x)
        double[] lnX = new double[x.length];
        double[] lnY = new double[y.length];
        
        for (int i = 0; i < y.length; i++) {
            if (x[i] <= 0 || y[i] <= 0) throw new IllegalArgumentException("Valores deben ser positivos");
            lnX[i] = Math.log(x[i]);
            lnY[i] = Math.log(y[i]);
        }
        
        double[] coefLineal = RegresionLinealSimple.calcular(lnX, lnY);
        double a = Math.exp(coefLineal[0]); // a = e^intercepto
        double b = coefLineal[1];           // b = pendiente
        
        return new double[]{a, b}; // y = a * x^b
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {1.5, 4.2, 8.7, 15.3, 24.1}; // Datos aproximadamente potenciales
        
        double[] coef = calcular(x, y);
        System.out.printf("Ecuación: y = %.3f * x^%.3f\n", coef[0], coef[1]);
        // Ejemplo: y = 1.2345 * x^1.5678
    }
}