import java.text.DecimalFormat;

public class L3{
    public static double interpolar(double x0, double y0, double x1, double y1, double x) {
        if (x0 == x1) throw new IllegalArgumentException("x0 y x1 no pueden ser iguales");
        if (x < x0 || x > x1) System.out.println("Advertencia: Extrapolando");
        return y0 + ((x - x0) * (y1 - y0)) / (x1 - x0);
    }

    public static void main(String[] args) {
        DecimalFormat df = new DecimalFormat("0.000");
        System.out.println("y(3) = " + df.format(interpolar(2, 4, 5, 10, 3))); // y(3) = 6.000
    }
}