import java.text.DecimalFormat;

public class P3 {
    public static String getPolinomio(double[] x, double[] y) {
        StringBuilder polinomio = new StringBuilder("P(x) = ");
        for (int i = 0; i < x.length; i++) {
            if (i > 0) polinomio.append(" + ");
            polinomio.append(y[i]);
            for (int j = 0; j < x.length; j++) {
                if (i != j) {
                    polinomio.append(String.format("*(x-%.1f)/%.1f", x[j], (x[i]-x[j])));
                }
            }
        }
        return polinomio.toString();
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3};
        double[] y = {1, 4, 9};
        System.out.println(getPolinomio(x, y));
        // P(x) = 1.0*(x-2.0)/-1.0*(x-3.0)/-2.0 + 4.0*(x-1.0)/1.0*(x-3.0)/-1.0 + 9.0*(x-1.0)/2.0*(x-2.0)/1.0
    }
}