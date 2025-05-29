// Bisección en Java
public class E1 {
    public static void main(String[] args) {
        try {
            double root = bisection(0, 3, 1e-6);
            System.out.println("La raíz encontrada es: " + String.format("%.3f", root)); // Trunca a 3 decimales
        } catch (IllegalArgumentException e) {
            System.out.println(e.getMessage());
        }
    }

    public static double bisection(double a, double b, double error) {
        if (f(a) * f(b) >= 0) {
            throw new IllegalArgumentException("La función debe tener signos opuestos en los extremos del intervalo");
        }
        
        while (Math.abs(b - a) > error) {
            double c = (a + b) / 2;
            double fc = f(c);
            
            if (Math.abs(fc) < 1e-12) {
                return c;
            }
            
            if (f(a) * fc < 0) {
                b = c;
            } else {
                a = c;
            }
        }
        return (a + b) / 2;
    }

    public static double f(double x) {
        return x * x - 5;
    }
}