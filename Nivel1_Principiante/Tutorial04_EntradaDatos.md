/**
 * TUTORIAL 4: ENTRADA DE DATOS - CAMPOS DE TEXTO
 * 
 * En este tutorial aprenderemos:
 * - ¿Qué es un JTextField?
 * - Cómo obtener texto que escribe el usuario
 * - Convertir texto a números
 * - Manejar errores básicos
 * - BorderLayout para organizar componentes
 * 
 * OBJETIVO: Crear una calculadora simple de suma
 */

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class Tutorial04_EntradaDatos {
    
    // PASO 1: VARIABLES DE INSTANCIA
    // Necesitamos guardar referencias a los componentes para usarlos después
    private JFrame ventana;
    private JTextField campoNumero1;      // Campo para el primer número
    private JTextField campoNumero2;      // Campo para el segundo número
    private JLabel etiquetaResultado;     // Para mostrar el resultado
    
    // PASO 2: CONSTRUCTOR
    public Tutorial04_EntradaDatos() {
        crearInterfaz();
    }
    
    private void crearInterfaz() {
        
        // PASO 3: CREAR LA VENTANA
        ventana = new JFrame("Calculadora Simple - Entrada de Datos");
        ventana.setSize(400, 250);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setLocationRelativeTo(null);
        
        // PASO 4: USAR BORDERLAYOUT
        // BorderLayout divide la ventana en 5 áreas:
        // NORTH (arriba), SOUTH (abajo), EAST (derecha), WEST (izquierda), CENTER (centro)
        ventana.setLayout(new BorderLayout());
        
        // PASO 5: CREAR EL PANEL SUPERIOR CON INSTRUCCIONES
        JPanel panelSuperior = new JPanel();
        JLabel instrucciones = new JLabel("Ingresa dos números y presiona SUMAR");
        instrucciones.setFont(new Font("Arial", Font.BOLD, 14));
        panelSuperior.add(instrucciones);
        
        // PASO 6: CREAR EL PANEL CENTRAL PARA LOS CAMPOS DE ENTRADA
        JPanel panelCentral = new JPanel(new GridLayout(3, 2, 10, 10));
        // GridLayout(filas, columnas, espacio horizontal, espacio vertical)
        
        // PASO 7: CREAR ETIQUETAS Y CAMPOS DE TEXTO
        
        // Primera fila: etiqueta y campo para el primer número
        JLabel etiqueta1 = new JLabel("Primer número:");
        campoNumero1 = new JTextField();       // JTextField para que el usuario escriba
        campoNumero1.setFont(new Font("Arial", Font.PLAIN, 16));  // Letra más grande
        
        // Segunda fila: etiqueta y campo para el segundo número  
        JLabel etiqueta2 = new JLabel("Segundo número:");
        campoNumero2 = new JTextField();
        campoNumero2.setFont(new Font("Arial", Font.PLAIN, 16));
        
        // Tercera fila: etiqueta para el resultado
        JLabel etiquetaTextoResultado = new JLabel("Resultado:");
        etiquetaResultado = new JLabel("---");     // Inicialmente muestra "---"
        etiquetaResultado.setFont(new Font("Arial", Font.BOLD, 16));
        
        // PASO 8: AGREGAR COMPONENTES AL PANEL CENTRAL
        panelCentral.add(etiqueta1);
        panelCentral.add(campoNumero1);
        panelCentral.add(etiqueta2);
        panelCentral.add(campoNumero2);
        panelCentral.add(etiquetaTextoResultado);
        panelCentral.add(etiquetaResultado);
        
        // PASO 9: CREAR EL PANEL INFERIOR CON EL BOTÓN
        JPanel panelInferior = new JPanel();
        JButton botonSumar = new JButton("SUMAR");
        botonSumar.setFont(new Font("Arial", Font.BOLD, 16));
        botonSumar.setPreferredSize(new Dimension(120, 40));  // Hacer el botón más grande
        
        // PASO 10: PROGRAMAR EL BOTÓN
        botonSumar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                realizarSuma();
            }
        });
        
        panelInferior.add(botonSumar);
        
        // PASO 11: AGREGAR PANELES A LA VENTANA USANDO BORDERLAYOUT
        ventana.add(panelSuperior, BorderLayout.NORTH);    // Arriba
        ventana.add(panelCentral, BorderLayout.CENTER);    // Centro
        ventana.add(panelInferior, BorderLayout.SOUTH);    // Abajo
        
        // PASO 12: MOSTRAR LA VENTANA
        ventana.setVisible(true);
    }
    
    // PASO 13: MÉTODO SEPARADO PARA REALIZAR LA SUMA
    // Es buena práctica separar la lógica en métodos diferentes
    private void realizarSuma() {
        try {
            // PASO 14: OBTENER EL TEXTO DE LOS CAMPOS
            // getText() obtiene lo que escribió el usuario
            String texto1 = campoNumero1.getText();
            String texto2 = campoNumero2.getText();
            
            // PASO 15: CONVERTIR TEXTO A NÚMEROS
            // Integer.parseInt() convierte texto a número entero
            // Double.parseDouble() convierte texto a número decimal
            double numero1 = Double.parseDouble(texto1);
            double numero2 = Double.parseDouble(texto2);
            
            // PASO 16: REALIZAR LA OPERACIÓN
            double resultado = numero1 + numero2;
            
            // PASO 17: MOSTRAR EL RESULTADO
            // String.format("%.2f", numero) muestra el número con 2 decimales
            etiquetaResultado.setText(String.format("%.2f", resultado));
            
        } catch (NumberFormatException ex) {
            // PASO 18: MANEJAR ERRORES
            // Si el usuario escribió algo que no es un número, llegamos aquí
            // NumberFormatException = "Error de formato de número"
            
            // Mostrar mensaje de error
            etiquetaResultado.setText("ERROR");
            
            // Mostrar mensaje emergente explicando el error
            JOptionPane.showMessageDialog(ventana, 
                "Por favor, ingresa solo números válidos.\n" +
                "Ejemplos: 5, 3.14, -2.5", 
                "Error de entrada", 
                JOptionPane.ERROR_MESSAGE);
        }
    }
    
    public static void main(String[] args) {
        new Tutorial04_EntradaDatos();
    }
}

/*
 * CONCEPTOS NUEVOS QUE ACABAS DE APRENDER:
 * 
 * 1. JTextField:
 *    - Permite al usuario escribir texto
 *    - getText() obtiene el texto escrito
 *    - setText() cambia el texto mostrado
 *    - setFont() cambia la apariencia del texto
 * 
 * 2. BorderLayout:
 *    - Divide la ventana en 5 áreas: NORTH, SOUTH, EAST, WEST, CENTER
 *    - ventana.add(componente, BorderLayout.NORTH)
 *    - Muy útil para interfaces organizadas
 * 
 * 3. Conversión de tipos:
 *    - Integer.parseInt() - texto a entero
 *    - Double.parseDouble() - texto a decimal
 *    - String.valueOf() - número a texto
 *    - String.format() - formatear números
 * 
 * 4. Manejo de errores (try-catch):
 *    - try { } - código que puede fallar
 *    - catch (TipoDeError ex) { } - qué hacer si falla
 *    - NumberFormatException - error al convertir texto a número
 * 
 * 5. JOptionPane con tipos de mensaje:
 *    - JOptionPane.ERROR_MESSAGE - mensaje de error
 *    - JOptionPane.INFORMATION_MESSAGE - mensaje informativo
 *    - JOptionPane.WARNING_MESSAGE - mensaje de advertencia
 * 
 * 6. Separación de responsabilidades:
 *    - crearInterfaz() - solo crea la interfaz
 *    - realizarSuma() - solo hace los cálculos
 *    - Cada método tiene una responsabilidad específica
 * 
 * FLUJO DEL PROGRAMA:
 * 1. Usuario escribe números en los campos
 * 2. Usuario presiona el botón SUMAR
 * 3. Se ejecuta realizarSuma()
 * 4. Se obtiene el texto de los campos
 * 5. Se convierte el texto a números
 * 6. Se realiza la suma
 * 7. Se muestra el resultado
 * 8. Si hay error, se muestra mensaje de error
 * 
 * EXPERIMENTACIÓN:
 * - Agrega botones para restar, multiplicar y dividir
 * - Agrega un botón "LIMPIAR" que borre los campos
 * - Haz que al presionar Enter en un campo se ejecute la suma
 * - Agrega validación para división por cero
 * - Cambia los colores de los campos de texto
 * - ¿Qué pasa si escribes letras en lugar de números?
 * - ¿Qué pasa si dejas un campo vacío?
 */