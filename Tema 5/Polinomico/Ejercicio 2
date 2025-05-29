import java.text.DecimalFormat;

public class P2
    private static final DecimalFormat df = new DecimalFormat("0.0000");

    public static class ResultadoInterpolacion {
        public final double valor;
        public final String ecuacion;
        
        public ResultadoInterpolacion(double valor, String ecuacion) {
            this.valor = valor;
            this.ecuacion = ecuacion;
        }
    }

    public static ResultadoInterpolacion lagrangeCompleto(double[] x, double[] y, double xTarget) {
        if (x.length != y.length) throw new IllegalArgumentException("Arrays deben tener igual longitud");
        if (x.length < 2) throw new IllegalArgumentException("Se necesitan al menos 2 puntos");

        StringBuilder ecuacion = new StringBuilder("P(x) = ");
        double resultado = 0;
        
        for (int i = 0; i < x.length; i++) {
            double termino = y[i];
            StringBuilder terminoStr = new StringBuilder();
            terminoStr.append(y[i]);
            
            for (int j = 0; j < x.length; j++) {
                if (i != j) {
                    if (x[i] == x[j]) throw new IllegalArgumentException("Valores x duplicados");
                    termino *= (xTarget - x[j]) / (x[i] - x[j]);
                    terminoStr.append(" * (x-").append(x[j]).append(")/").append(x[i]-x[j]);
                }
            }
            
            if (i > 0) ecuacion.append(" + ");
            ecuacion.append(terminoStr);
            resultado += termino;
        }
        
        return new ResultadoInterpolacion(resultado, ecuacion.toString());
    }

    public static void main(String[] args) {
        double[] x = {1, 2, 4};
        double[] y = {3, 1, 2};
        
        ResultadoInterpolacion res = lagrangeCompleto(x, y, 3);
        System.out.println("Ecuación: " + res.ecuacion);
        System.out.println("y(3) = " + df.format(res.valor)); // 1.6667
        
        // Visualización de los puntos
        System.out.println("\nPuntos conocidos:");
        for (int i = 0; i < x.length; i++) {
            System.out.printf("(%.0f, %.0f)%n", x[i], y[i]);
        }
    }
}