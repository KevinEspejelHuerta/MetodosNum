public class C1 {
    public static void main(String[] args) {
        double x = Math.PI / 3;
        double h = 0.0001;
        double derivada = (-f(x + 2*h) + 8*f(x + h) - 8*f(x - h) + f(x - 2*h)) / (12*h);
        System.out.println("Derivada de cos(x) en π/3: " + String.format("%.6f", derivada));
    }

    public static double f(double x) {
        return Math.cos(x);
    }
}