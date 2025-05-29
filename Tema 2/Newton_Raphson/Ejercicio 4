// Newton-Raphson en Java
public class N4{

    public static void main(String[] args) {
        try {
            double initialGuess = 2.5;  // Aproximación inicial (x₀)
            double tolerance = 1e-6;    // Tolerancia de error (1×10⁻⁶)
            
            double root = newtonRaphson(initialGuess, tolerance);
            
            System.out.println("Raíz encontrada: " + String.format("%.6f", root));
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    public static double newtonRaphson(double x0, double error) {
        double x1;  // Almacenará la nueva aproximación
        
        do {
            double derivative = df(x0);
            
            // Evitar división por cero (si la derivada es cero)
            if (Math.abs(derivative) < 1e-12) {
                throw new IllegalArgumentException("Derivada cero en x = " + x0);
            }
            
            // Fórmula de Newton-Raphson: x₁ = x₀ - f(x₀)/f'(x₀)
            x1 = x0 - f(x0) / derivative;
            
            // Actualizar la aproximación para la siguiente iteración
            x0 = x1;
            
        } while (Math.abs(f(x1)) > error);  // Continuar hasta alcanzar la precisión deseada
        
        return x1;
    }

   public static double f(double x) {
    return Math.sin(x) + x * Math.cos(x);
}
public static double df(double x) {
    return 2 * Math.cos(x) - x * Math.sin(x);
}
}