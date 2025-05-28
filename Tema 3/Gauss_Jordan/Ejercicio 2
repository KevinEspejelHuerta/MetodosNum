package com.mycompany.gauss.jordan3;

import java.util.Scanner;

public class GaussJordan3 {

    public static void main(String[] args) {
   Scanner scanner = new Scanner(System.in);
        System.out.println("Ingrese el tamaño de la matriz cuadrada (n x n): ");
        int n = scanner.nextInt();
        
        double[][] matriz = new double[n][n+1];
        
        System.out.println("Ingrese los elementos de la matriz extendida (separados por espacios y por fila): ");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n+1; j++) {
                matriz[i][j] = scanner.nextDouble();
            }
        }
        
        double[][] resultados = operaciones(matriz);
        Resultados(resultados);
        
        scanner.close();
    }

    public static double[][] operaciones(double[][] matriz) {
        int fila = matriz.length;
        int columna = matriz[0].length;
        for (int i = 0; i < fila; i++) {
            double pivote = matriz[i][i];
            for (int j = i + 1; j < columna; j++) {
                matriz[i][j] /= pivote;
            }
            matriz[i][i] = 1;
            for (int j = 0; j < fila; j++) {
                if (i != j) {
                    double epala = matriz[j][i];
                    for (int k = i; k < columna; k++) {
                        matriz[j][k] -= epala * matriz[i][k];
                    }
                }
            }
        }
        return matriz;
    }

    public static void Resultados(double[][] matriz) {
        System.out.println("Los resultados son: ");
        for (int i = 0; i < matriz.length; i++) {
            System.out.println((char)('X' + i) + " = " + matriz[i][matriz[i].length - 1]);
        }
    }
}