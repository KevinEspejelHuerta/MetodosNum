import java.util.Arrays;
import java.util.Comparator;

public class C3 {
    private static double[] asignarRangos(double[] datos) {
        Integer[] indices = new Integer[datos.length];
        for (int i = 0; i < datos.length; i++) indices[i] = i;
        
        Arrays.sort(indices, Comparator.comparingDouble(i -> datos[i]));
        
        double[] rangos = new double[datos.length];
        for (int i = 0; i < datos.length; i++) {
            rangos[indices[i]] = i + 1;
        }
        return rangos;
    }

    public static double calcular(double[] x, double[] y) {
        double[] rangosX = asignarRangos(x);
        double[] rangosY = asignarRangos(y);
        return CorrelacionPearson.calcular(rangosX, rangosY);
    }

    public static void main(String[] args) {
        double[] x = {10, 20, 30, 40, 50};
        double[] y = {2, 4, 6, 8, 10};
        double rho = calcular(x, y);
        System.out.println("Correlación Spearman: " + new DecimalFormat("0.000").format(rho)); // 1.000
    }
}