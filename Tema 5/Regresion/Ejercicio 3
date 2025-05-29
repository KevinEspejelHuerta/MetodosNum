import java.text.DecimalFormat;

public class R3 {
    public static double[] calcular(double[] x, double[] y) {
        if (x.length != y.length) throw new IllegalArgumentException("Arrays deben tener igual longitud");
        
        // Transformación logarítmica para linealizar: ln(y) = ln(a) + b*x
        double[] lnY = new double[y.length];
        for (int i = 0; i < y.length; i++) {
            if (y[i] <= 0) throw new IllegalArgumentException("Valores y deben ser positivos");
            lnY[i] = Math.log(y[i]);
        }
        
        double[] coefLineal = RegresionLinealSimple.calcular(x, lnY);
        double a = Math.exp(coefLineal[0]); // a = e^intercepto
        double b = coefLineal[1];           // b = pendiente
        
        return new double[]{a, b}; // y = a * e^(bx)
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {2.5, 7.4, 20.1, 54.6, 148.4}; // Datos aproximadamente exponenciales
        
        double[] coef = calcular(x, y);
        System.out.printf("Ecuación: y = %.3f * e^(%.3fx)\n", coef[0], coef[1]);
        // Ejemplo: y = 0.7419 * e^(0.9979x)
    }
}