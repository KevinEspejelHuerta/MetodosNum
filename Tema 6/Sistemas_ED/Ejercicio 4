package Sistemas_ED;

public class S4 {
    public interface Aceleracion {
        double[] calcular(double[] posicion);
    }

    public static double[][] resolver(Aceleracion aceleracion,
                                    double[] pos0, double[] vel0, 
                                    double t0, double tf, double h) {
        int n = pos0.length;
        int pasos = (int) ((tf - t0) / h);
        double[][] trayectoria = new double[pasos + 1][2 * n]; // [pos, vel]

        // Condiciones iniciales
        System.arraycopy(pos0, 0, trayectoria[0], 0, n);
        System.arraycopy(vel0, 0, trayectoria[0], n, n);

        // Primer paso con Euler modificado
        double[] a0 = aceleracion.calcular(pos0);
        for (int j = 0; j < n; j++) {
            trayectoria[1][j] = pos0[j] + h * vel0[j] + 0.5 * h * h * a0[j]; // pos
            trayectoria[1][n + j] = vel0[j] + h * a0[j]; // vel
        }

        // Pasos siguientes con Verlet
        for (int i = 2; i <= pasos; i++) {
            double[] posActual = new double[n];
            double[] posPrev = new double[n];
            for (int j = 0; j < n; j++) {
                posPrev[j] = trayectoria[i-2][j];
                posActual[j] = trayectoria[i-1][j];
            }

            double[] a = aceleracion.calcular(posActual);
            for (int j = 0; j < n; j++) {
                // Actualizar posición
                trayectoria[i][j] = 2 * posActual[j] - posPrev[j] + h * h * a[j];
                // Actualizar velocidad (opcional)
                trayectoria[i][n + j] = (trayectoria[i][j] - posPrev[j]) / (2 * h);
            }
        }
        return trayectoria;
    }

    public static void main(String[] args) {
        // Ejemplo: Órbita planetaria (fuerza central)
        Aceleracion aceleracion = pos -> {
            double r = Math.sqrt(pos[0]*pos[0] + pos[1]*pos[1]);
            double k = -1.0; // Constante gravitacional simplificada
            return new double[]{
                k * pos[0] / (r * r * r),
                k * pos[1] / (r * r * r)
            };
        };

        double[] pos0 = {1.0, 0.0};  // Posición inicial (x, y)
        double[] vel0 = {0.0, 0.8};  // Velocidad inicial (vx, vy)
        double[][] orbita = resolver(aceleracion, pos0, vel0, 0.0, 10.0, 0.01);

        System.out.printf("Posición final: x=%.4f, y=%.4f%n",
            orbita[orbita.length-1][0], orbita[orbita.length-1][1]);
    }
}