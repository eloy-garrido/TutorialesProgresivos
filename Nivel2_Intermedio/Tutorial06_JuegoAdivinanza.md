# Tutorial 06: Juego de Adivinanza Simple

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- Generar números aleatorios con Random
- Lógica condicional más compleja (if-else anidados)
- Validación de entrada del usuario
- Control básico del estado del juego
- Tu primer juego completo!

**OBJETIVO FINAL:** Crear un juego donde el usuario adivine un número del 1 al 10

---

## 🎮 Cómo Funcionará el Juego

1. **La computadora** piensa un número secreto del 1 al 10
2. **El usuario** escribe su adivinanza en un campo de texto
3. **El programa** dice si es "muy alto", "muy bajo" o "correcto"
4. **El usuario** sigue intentando hasta adivinar
5. **El programa** cuenta cuántos intentos necesitó

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial06_JuegoAdivinanza.java`:

```java
/**
 * TUTORIAL 6: JUEGO DE ADIVINANZA SIMPLE
 * 
 * En este tutorial aprenderemos:
 * - Generar números aleatorios con Random
 * - Lógica condicional más compleja
 * - Validación de entrada del usuario
 * - Control básico del estado del juego
 * 
 * OBJETIVO: Crear un juego donde el usuario adivine un número del 1 al 10
 */

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.util.Random;  // Para generar números aleatorios

public class Tutorial06_JuegoAdivinanza {
    
    // PASO 1: VARIABLES DE INSTANCIA PARA LA INTERFAZ
    private JFrame ventana;
    private JTextField campoNumero;
    private JButton botonAdivinar;
    private JButton botonNuevoJuego;
    private JLabel etiquetaInstrucciones;
    private JLabel etiquetaResultado;
    private JLabel etiquetaIntentos;
    
    // PASO 2: VARIABLES PARA LA LÓGICA DEL JUEGO
    private Random generadorAleatorio;    // Para generar números aleatorios
    private int numeroSecreto;           // El número que el usuario debe adivinar
    private int intentos;                // Cuántos intentos ha hecho el usuario
    
    // PASO 3: CONSTRUCTOR
    public Tutorial06_JuegoAdivinanza() {
        generadorAleatorio = new Random();  // Inicializar el generador de números aleatorios
        empezarNuevoJuego();                // Generar el primer número secreto
        crearInterfaz();
    }
    
    private void crearInterfaz() {
        
        // PASO 4: CREAR LA VENTANA PRINCIPAL
        ventana = new JFrame("🎯 Juego de Adivinanza - ¡Adivina el número!");
        ventana.setSize(400, 300);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setLocationRelativeTo(null);
        ventana.setLayout(new BorderLayout());
        
        // PASO 5: PANEL SUPERIOR - TÍTULO E INSTRUCCIONES
        JPanel panelSuperior = new JPanel(new GridLayout(2, 1));
        
        JLabel titulo = new JLabel("🎯 ADIVINA EL NÚMERO 🎯", JLabel.CENTER);
        titulo.setFont(new Font("Arial", Font.BOLD, 18));
        titulo.setForeground(Color.BLUE);
        
        etiquetaInstrucciones = new JLabel("He pensado un número del 1 al 10. ¡Adivínalo!", JLabel.CENTER);
        etiquetaInstrucciones.setFont(new Font("Arial", Font.PLAIN, 12));
        
        panelSuperior.add(titulo);
        panelSuperior.add(etiquetaInstrucciones);
        
        // PASO 6: PANEL CENTRAL - ENTRADA Y BOTONES
        JPanel panelCentral = new JPanel(new GridLayout(3, 1, 10, 10));
        panelCentral.setBorder(BorderFactory.createEmptyBorder(30, 50, 30, 50));
        
        // PASO 7: CAMPO PARA INGRESAR EL NÚMERO
        JLabel etiquetaCampo = new JLabel("Tu adivinanza (1-10):", JLabel.CENTER);
        etiquetaCampo.setFont(new Font("Arial", Font.BOLD, 14));
        
        campoNumero = new JTextField();
        campoNumero.setFont(new Font("Arial", Font.BOLD, 20));
        campoNumero.setHorizontalAlignment(JTextField.CENTER);
        
        // PASO 8: BOTONES
        JPanel panelBotones = new JPanel(new GridLayout(1, 2, 10, 0));
        
        botonAdivinar = new JButton("🤔 ADIVINAR");
        botonAdivinar.setFont(new Font("Arial", Font.BOLD, 14));
        botonAdivinar.setBackground(new Color(0, 150, 0));
        botonAdivinar.setForeground(Color.WHITE);
        
        botonNuevoJuego = new JButton("🔄 NUEVO JUEGO");
        botonNuevoJuego.setFont(new Font("Arial", Font.BOLD, 14));
        botonNuevoJuego.setBackground(new Color(200, 100, 0));
        botonNuevoJuego.setForeground(Color.WHITE);
        
        panelBotones.add(botonAdivinar);
        panelBotones.add(botonNuevoJuego);
        
        // PASO 9: PROGRAMAR LOS BOTONES
        botonAdivinar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                procesarAdivinanza();
            }
        });
        
        botonNuevoJuego.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                empezarNuevoJuego();
                actualizarInterfaz();
            }
        });
        
        panelCentral.add(etiquetaCampo);
        panelCentral.add(campoNumero);
        panelCentral.add(panelBotones);
        
        // PASO 10: PANEL INFERIOR - RESULTADOS
        JPanel panelInferior = new JPanel(new GridLayout(2, 1));
        
        etiquetaResultado = new JLabel("¡Haz tu primera adivinanza!", JLabel.CENTER);
        etiquetaResultado.setFont(new Font("Arial", Font.BOLD, 16));
        
        etiquetaIntentos = new JLabel("Intentos: 0", JLabel.CENTER);
        etiquetaIntentos.setFont(new Font("Arial", Font.BOLD, 14));
        etiquetaIntentos.setForeground(Color.GRAY);
        
        panelInferior.add(etiquetaResultado);
        panelInferior.add(etiquetaIntentos);
        
        // PASO 11: AGREGAR PANELES A LA VENTANA
        ventana.add(panelSuperior, BorderLayout.NORTH);
        ventana.add(panelCentral, BorderLayout.CENTER);
        ventana.add(panelInferior, BorderLayout.SOUTH);
        
        ventana.setVisible(true);
        campoNumero.requestFocus(); // Poner el cursor en el campo de texto
    }
    
    // PASO 12: MÉTODO PARA EMPEZAR UN NUEVO JUEGO
    private void empezarNuevoJuego() {
        // PASO 13: GENERAR NÚMERO ALEATORIO DEL 1 AL 10
        // nextInt(10) genera números de 0 a 9
        // Sumamos 1 para obtener números de 1 a 10
        numeroSecreto = generadorAleatorio.nextInt(10) + 1;
        
        intentos = 0;  // Reiniciar contador de intentos
        
        // Para debugging puedes descomentar esta línea (pero es trampa 😉):
        // System.out.println("Número secreto: " + numeroSecreto);
    }
    
    // PASO 14: MÉTODO PARA PROCESAR LA ADIVINANZA DEL USUARIO
    private void procesarAdivinanza() {
        
        try {
            // PASO 15: OBTENER Y VALIDAR EL NÚMERO INGRESADO
            String textoIngresado = campoNumero.getText().trim();
            
            // PASO 16: VERIFICAR QUE NO ESTÉ VACÍO
            if (textoIngresado.isEmpty()) {
                mostrarError("Por favor, ingresa un número.");
                return;
            }
            
            // PASO 17: CONVERTIR TEXTO A NÚMERO
            int numeroUsuario = Integer.parseInt(textoIngresado);
            
            // PASO 18: VALIDAR QUE ESTÉ EN EL RANGO CORRECTO (1-10)
            if (numeroUsuario < 1 || numeroUsuario > 10) {
                mostrarError("El número debe estar entre 1 y 10.");
                return;
            }
            
            // PASO 19: INCREMENTAR CONTADOR DE INTENTOS
            intentos++;
            etiquetaIntentos.setText("Intentos: " + intentos);
            
            // PASO 20: COMPARAR CON EL NÚMERO SECRETO
            if (numeroUsuario == numeroSecreto) {
                // ¡GANÓ!
                etiquetaResultado.setText("🎉 ¡CORRECTO! ¡Ganaste en " + intentos + " intentos!");
                etiquetaResultado.setForeground(new Color(0, 150, 0));
                
                // Mensaje especial según el número de intentos
                String mensaje = obtenerMensajeVictoria(intentos);
                JOptionPane.showMessageDialog(ventana, mensaje, "¡GANASTE!", JOptionPane.INFORMATION_MESSAGE);
                
            } else if (numeroUsuario < numeroSecreto) {
                // Número muy bajo
                etiquetaResultado.setText("📈 ¡Muy bajo! Intenta con un número mayor.");
                etiquetaResultado.setForeground(Color.RED);
                
            } else {
                // Número muy alto
                etiquetaResultado.setText("📉 ¡Muy alto! Intenta con un número menor.");
                etiquetaResultado.setForeground(Color.RED);
            }
            
            // PASO 21: LIMPIAR EL CAMPO PARA EL SIGUIENTE INTENTO
            campoNumero.setText("");
            campoNumero.requestFocus();
            
        } catch (NumberFormatException ex) {
            // PASO 22: MANEJAR ERROR SI NO ES UN NÚMERO
            mostrarError("Por favor, ingresa solo números enteros (ejemplo: 1, 2, 3...)");
        }
    }
    
    // PASO 23: MÉTODO AUXILIAR PARA MOSTRAR MENSAJES DE ERROR
    private void mostrarError(String mensaje) {
        JOptionPane.showMessageDialog(ventana, mensaje, "Error", JOptionPane.WARNING_MESSAGE);
        campoNumero.requestFocus(); // Poner el cursor de vuelta en el campo
    }
    
    // PASO 24: MÉTODO PARA GENERAR MENSAJE DE VICTORIA SEGÚN INTENTOS
    private String obtenerMensajeVictoria(int intentos) {
        if (intentos == 1) {
            return "¡INCREÍBLE! ¡Lo adivinaste al primer intento! 🏆";
        } else if (intentos <= 3) {
            return "¡Excelente! Muy pocos intentos. 🌟";
        } else if (intentos <= 5) {
            return "¡Bien hecho! Un buen resultado. 👍";
        } else {
            return "¡Felicidades! Finalmente lo lograste. 😊";
        }
    }
    
    // PASO 25: MÉTODO PARA ACTUALIZAR LA INTERFAZ AL REINICIAR
    private void actualizarInterfaz() {
        etiquetaResultado.setText("¡Haz tu primera adivinanza!");
        etiquetaResultado.setForeground(Color.BLACK);
        etiquetaIntentos.setText("Intentos: 0");
        campoNumero.setText("");
        campoNumero.requestFocus();
    }
    
    // PASO 26: MÉTODO MAIN
    public static void main(String[] args) {
        new Tutorial06_JuegoAdivinanza();
    }
}
```

---

## 🔍 **Conceptos Nuevos Que Acabas de Aprender:**

### 1. **RANDOM (Números Aleatorios):**
```java
Random generadorAleatorio = new Random();
int numeroSecreto = generadorAleatorio.nextInt(10) + 1;
```
- `Random` es una clase para generar números aleatorios
- `nextInt(10)` genera números de **0 a 9**
- Sumamos **1** para obtener números de **1 a 10**

### 2. **VALIDACIÓN DE ENTRADA:**
```java
if (textoIngresado.isEmpty()) {
    mostrarError("Por favor, ingresa un número.");
    return;
}
```
- Siempre **verificar que el usuario escribió algo**
- **Verificar rangos** de números válidos
- **Dar mensajes de error claros**

### 3. **TRY-CATCH (Manejo de Errores):**
```java
try {
    int numeroUsuario = Integer.parseInt(textoIngresado);
} catch (NumberFormatException ex) {
    mostrarError("Por favor, ingresa solo números...");
}
```
- **try** = "intenta ejecutar este código"
- **catch** = "si hay error, haz esto"
- **NumberFormatException** = error al convertir texto a número

### 4. **MÉTODOS AUXILIARES:**
```java
private String obtenerMensajeVictoria(int intentos) {
    if (intentos == 1) {
        return "¡INCREÍBLE!...";
    }
    // más código...
}
```
- **Dividir el código** en métodos más pequeños
- Cada método **hace una sola cosa**
- Hace el código **más fácil de leer**

### 5. **SETFOREGROUND() - Colores:**
```java
etiquetaResultado.setForeground(Color.GREEN);  // Verde para éxito
etiquetaResultado.setForeground(Color.RED);    // Rojo para error
```
- Cambia el **color del texto**
- **Verde** para mensajes positivos
- **Rojo** para mensajes de error

---

## 🎮 **Flujo del Juego:**

1. **Programa genera** número secreto del 1 al 10
2. **Usuario escribe** su adivinanza
3. **Usuario presiona** "ADIVINAR"
4. **Programa valida** la entrada (¿es número? ¿está en rango?)
5. **Programa compara** con el número secreto
6. **Programa da pista:** "muy alto", "muy bajo" o "correcto"
7. **Si adivinó:** muestra mensaje de victoria
8. **Si no:** usuario puede seguir intentando
9. **Usuario puede** empezar un nuevo juego cuando quiera

---

## 🧪 **Experimentación Sugerida:**

### Cambios Básicos:
1. **Cambiar el rango** a números del 1 al 20
2. **Modificar mensajes** de victoria con tus propias palabras
3. **Cambiar colores** de los botones y texto
4. **Agregar más emojis** a los mensajes

### Mejoras Intermedias:
5. **Límite de intentos:** El usuario solo tiene 5 intentos
6. **Puntuación:** Dar más puntos si adivina en menos intentos
7. **Mejor feedback:** "¡Muy cerca!" si está a ±1 del número
8. **Validación extra:** No permitir el mismo número dos veces

### Desafíos Avanzados:
9. **Historial:** Mostrar todos los números que ya intentó
10. **Niveles de dificultad:** Fácil (1-10), Medio (1-50), Difícil (1-100)
11. **Contador de victorias:** Cuántos juegos ha ganado en total
12. **Mejor tiempo:** Guardar el menor número de intentos

---

## ✅ **Verificación de Comprensión**

Antes de continuar, asegúrate de que puedes:

- ✅ **Explicar** cómo funciona `Random.nextInt()`
- ✅ **Usar** try-catch para manejar errores
- ✅ **Validar** entrada del usuario (vacío, rango, tipo)
- ✅ **Cambiar** colores de texto dinámicamente
- ✅ **Crear** métodos auxiliares para organizar código
- ✅ **Entender** el flujo completo del juego

---

## 🚀 **Siguiente Paso**

¡Increíble! Ya creaste tu **primer juego completo** con validación, números aleatorios y manejo de errores. 

En el próximo tutorial daremos el gran salto a crear el famoso juego **Piedra, Papel y Tijera** con múltiples opciones y lógica más compleja.

**Próximo:** Tutorial 07 - Piedra, Papel y Tijera