public class C3 {
    public static void main(String[] args) {
        double x = 1;
        double h = 0.0001;
        double derivada = (-f(x + 2*h) + 8*f(x + h) - 8*f(x - h) + f(x - 2*h)) / (12*h);
        System.out.println("Derivada de ln(x) en 1: " + String.format("%.6f", derivada));
    }

    public static double f(double x) {
        return x * Math.exp(x);
    }
}