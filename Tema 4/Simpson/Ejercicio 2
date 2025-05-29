public class S2 {
    public static void main(String[] args) {
        double a = 0, b = 2;
        int n = 100;
        double integral = simpson(a, b, n);
        System.out.println("Integral de x² en [0,2]: " + String.format("%.6f", integral));
    }

    public static double simpson(double a, double b, int n) {
        if (n % 2 != 0) throw new IllegalArgumentException("n debe ser par");
        double h = (b - a) / n;
        double sum = f(a) + f(b);
        for (int i = 1; i < n; i++) {
            sum += (i % 2 == 0 ? 2 : 4) * f(a + i * h);
        }
        return (h / 3) * sum;
    }

    public static double f(double x) {
        return Math.sin(x);
    }
}