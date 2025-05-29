import java.text.DecimalFormat;

public class P1
    private static final DecimalFormat df = new DecimalFormat("0.0000");

    public static double lagrange(double[] x, double[] y, double xTarget) {
        if (x.length != y.length) throw new IllegalArgumentException("Arrays deben tener igual longitud");
        
        double resultado = 0;
        for (int i = 0; i < x.length; i++) {
            double termino = y[i];
            for (int j = 0; j < x.length; j++) {
                if (i != j) {
                    if (x[i] == x[j]) throw new IllegalArgumentException("Valores x duplicados");
                    termino *= (xTarget - x[j]) / (x[i] - x[j]);
                }
            }
            resultado += termino;
        }
        return resultado;
    }

    public static void main(String[] args) {
        double[] x = {1, 3, 5};
        double[] y = {4, 8, 6};
        
        System.out.println("y(2) = " + df.format(lagrange(x, y, 2))); // 6.6667
        System.out.println("y(4) = " + df.format(lagrange(x, y, 4))); // 7.3333
    }
}