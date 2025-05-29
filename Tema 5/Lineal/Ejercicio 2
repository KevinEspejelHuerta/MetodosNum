import java.text.DecimalFormat;

public class L2{
    private static final DecimalFormat df = new DecimalFormat("0.0000");

    public static double interpolar(double[] x, double[] y, double xTarget) {
        if (x.length != y.length) throw new IllegalArgumentException("Arrays deben tener igual longitud");
        if (x.length < 2) throw new IllegalArgumentException("Se necesitan al menos 2 puntos");
        
        for (int i = 0; i < x.length - 1; i++) {
            if (xTarget >= x[i] && xTarget <= x[i+1]) {
                return y[i] + (y[i+1] - y[i]) * (xTarget - x[i]) / (x[i+1] - x[i]);
            }
        }
        return xTarget < x[0] ? y[0] : y[y.length-1]; // Extrapolación
    }

    public static void main(String[] args) {
        double[] x = {0, 2, 5, 8};
        double[] y = {3, 7, 11, 19};
        
        System.out.println("y(1) = " + df.format(interpolar(x, y, 1)));   // 5.0000
        System.out.println("y(4) = " + df.format(interpolar(x, y, 4)));   // 9.6667
        System.out.println("y(10) = " + df.format(interpolar(x, y, 10))); // Extrapolación: 19.0000
    }
}