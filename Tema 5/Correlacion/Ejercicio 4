import java.text.DecimalFormat;

public class C4 {
    public static class Resultado {
        public final double r;
        public final String interpretacion;

        public Resultado(double r) {
            this.r = r;
            this.interpretacion = interpretarCorrelacion(r);
        }

        private String interpretarCorrelacion(double r) {
            double absR = Math.abs(r);
            if (absR >= 0.9) return "Correlación muy fuerte";
            else if (absR >= 0.7) return "Correlación fuerte";
            else if (absR >= 0.5) return "Correlación moderada";
            else if (absR >= 0.3) return "Correlación débil";
            else return "Correlación muy débil o nula";
        }
    }

    public static Resultado analizar(double[] x, double[] y) {
        double r = CorrelacionPearson.calcular(x, y);
        return new Resultado(r);
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 3, 4, 5};
        double[] y = {2, 3.9, 6.2, 7.8, 10.1};
        Resultado res = analizar(x, y);
        System.out.printf("r = %.3f (%s)\n", res.r, res.interpretacion); // r = 0.999 (Correlación muy fuerte)
    }
}