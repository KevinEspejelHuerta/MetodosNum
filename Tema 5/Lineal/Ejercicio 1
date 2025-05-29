import java.text.DecimalFormat;

public class L1{
    private static final DecimalFormat df = new DecimalFormat("0.0000");

    public static double interpolar(double x0, double y0, double x1, double y1, double x) {
        if (x0 == x1) throw new IllegalArgumentException("x0 y x1 no pueden ser iguales");
        return y0 + (y1 - y0) * (x - x0) / (x1 - x0);
    }

    public static void main(String[] args) {
        // Ejemplo: Puntos (1,2) y (4,5)
        double resultado = interpolar(1, 2, 4, 5, 2.5);
        System.out.println("y(2.5) = " + df.format(resultado)); // Debe dar 3.5
        
        // Caso de error
        try {
            interpolar(1, 2, 1, 5, 2);
        } catch (IllegalArgumentException e) {
            System.out.println("Error correctamente detectado: " + e.getMessage());
        }
    }
}