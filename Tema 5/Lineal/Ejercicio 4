import java.text.DecimalFormat;

public class L4 {
    public static class Resultado {
        public final double y;
        public final String ecuacion;

        public Resultado(double y, String ecuacion) {
            this.y = y;
            this.ecuacion = ecuacion;
        }
    }

    public static Resultado interpolar(double x0, double y0, double x1, double y1, double x) {
        double m = (y1 - y0)/(x1 - x0);
        double b = y0 - m*x0;
        return new Resultado(
            m*x + b,
            String.format("y = %.2f + %.2f*x", b, m)
        );
    }

    public static void main(String[] args) {
        Resultado res = interpolar(1, 1, 3, 9, 2);
        System.out.println(res.ecuacion); // y = -3.00 + 4.00*x
        System.out.printf("y(2) = %.3f%n", res.y); // y(2) = 5.000
    }
}