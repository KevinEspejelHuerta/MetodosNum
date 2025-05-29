// Falsa Posición en Java
public class FP1 {

    public static void main(String[] args) {
        try {
            // Llamamos al método falsePosition con intervalo [0, 3] y error máximo 1e-6
            double root = falsePosition(0, 3, 1e-6);
            // Mostramos el resultado formateado a 3 decimales
            System.out.println("Raíz encontrada: " + String.format("%.3f", root));
        } catch (IllegalArgumentException e) {
            // Capturamos y mostramos errores de intervalo inválido
            System.out.println("Error: " + e.getMessage());
        }
    }

    public static double falsePosition(double a, double b, double error) {
        // Verificamos que haya cambio de signo en los extremos del intervalo
        if (f(a) * f(b) >= 0) {
            throw new IllegalArgumentException("La función no cambia de signo en [a, b].");
        }

        double c = a; // Inicializamos el punto de aproximación

        // Iteramos hasta que el valor absoluto de f(c) sea menor que el error
        while (Math.abs(f(c)) > error) {
            // Calculamos el nuevo punto c usando la fórmula de la falsa posición
            c = (a * f(b) - b * f(a)) / (f(b) - f(a));

            // Si f(c) es prácticamente cero, terminamos la iteración
            if (Math.abs(f(c)) < 1e-12) {
                break;
            }

            // Actualizamos el intervalo según el signo de f(c)
            if (f(a) * f(c) < 0) {
                b = c; // La raíz está en el subintervalo izquierdo [a, c]
            } else {
                a = c; // La raíz está en el subintervalo derecho [c, b]
            }
        }

        return c; // Devolvemos la aproximación final de la raíz
    }

    public static double f(double x) {
        return x * x - 5;
    }
}