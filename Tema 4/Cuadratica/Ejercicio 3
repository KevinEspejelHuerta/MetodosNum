public class CU3 {
    public static void main(String[] args) {
        double a = -1, b = 1;
        double integral = cuadraturaGaussiana(a, b);
        System.out.println("Integral de x³ en [-1,1]: " + String.format("%.6f", integral));
    }

    public static double cuadraturaGaussiana(double a, double b) {
        double[] x = { -1/Math.sqrt(3), 1/Math.sqrt(3) };
        double[] w = { 1.0, 1.0 };
        double sum = 0;
        for (int i = 0; i < x.length; i++) {
            double xi = ((b - a) * x[i] + (a + b)) / 2;
            sum += w[i] * f(xi);
        }
        return ((b - a) / 2) * sum;
    }

    public static double f(double x) {
        return Math.exp(x);
    }
}