# Tutorial 04: Entrada de Datos - Campos de Texto

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- ¿Qué es un JTextField?
- Cómo obtener texto que escribe el usuario
- Convertir texto a números
- Manejar errores básicos
- BorderLayout para organizar componentes

**OBJETIVO FINAL:** Crear una calculadora simple de suma

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial04_EntradaDatos.java`:

```java
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
```

---

## 🔍 **Conceptos Importantes Que Acabas de Aprender:**

### 1. **JTextField** - Campos de Texto para Entrada del Usuario
```java
JTextField campoNumero1 = new JTextField();
```
- **JTextField** permite al usuario escribir texto
- **getText()** obtiene el texto que escribió el usuario
- **setText()** cambia el texto mostrado en el campo
- **setFont()** cambia la apariencia del texto

### 2. **BorderLayout** - Organización en 5 Áreas
```java
ventana.setLayout(new BorderLayout());
ventana.add(panelSuperior, BorderLayout.NORTH);    // Arriba
ventana.add(panelCentral, BorderLayout.CENTER);    // Centro  
ventana.add(panelInferior, BorderLayout.SOUTH);    // Abajo
```
- **BorderLayout** divide la ventana en 5 áreas:
  - **NORTH** (arriba)
  - **SOUTH** (abajo) 
  - **EAST** (derecha)
  - **WEST** (izquierda)
  - **CENTER** (centro)

### 3. **Conversión de Tipos** - De Texto a Números
```java
String texto1 = campoNumero1.getText();        // Obtener texto
double numero1 = Double.parseDouble(texto1);   // Convertir a número
String resultado = String.format("%.2f", suma); // Formatear resultado
```
- **Integer.parseInt()** - convierte texto a número entero
- **Double.parseDouble()** - convierte texto a número decimal
- **String.valueOf()** - convierte número a texto
- **String.format("%.2f", numero)** - formatea números con decimales

### 4. **Manejo de Errores** - try-catch
```java
try {
    // Código que puede fallar
    double numero = Double.parseDouble(texto);
} catch (NumberFormatException ex) {
    // Qué hacer si falla
    JOptionPane.showMessageDialog(ventana, "Error: ingresa un número válido");
}
```
- **try { }** - código que puede causar error
- **catch (TipoDeError ex) { }** - qué hacer si ocurre el error
- **NumberFormatException** - error específico al convertir texto a número

### 5. **JOptionPane con Tipos de Mensaje**
```java
JOptionPane.showMessageDialog(ventana, "mensaje", "título", JOptionPane.ERROR_MESSAGE);
```
- **JOptionPane.ERROR_MESSAGE** - mensaje de error (ícono rojo)
- **JOptionPane.INFORMATION_MESSAGE** - mensaje informativo (ícono azul)
- **JOptionPane.WARNING_MESSAGE** - mensaje de advertencia (ícono amarillo)

---

## 🎮 **Flujo del Programa:**

### **Secuencia de Eventos:**
1. **Usuario escribe números** en los campos de texto
2. **Usuario presiona el botón SUMAR**
3. **Se ejecuta realizarSuma()**
4. **Se obtiene el texto** de los campos con `getText()`
5. **Se convierte el texto a números** con `parseDouble()`
6. **Se realiza la suma**
7. **Se muestra el resultado** en la etiqueta
8. **Si hay error**, se muestra mensaje explicativo

### **Manejo de Errores:**
- Si el usuario escribe **letras** → Error de conversión
- Si el usuario deja un campo **vacío** → Error de conversión  
- Si el usuario escribe **símbolos extraños** → Error de conversión
- En todos los casos, se muestra un mensaje claro explicando el problema

---

## 🏗️ **Arquitectura del Código - Separación de Responsabilidades**

### **crearInterfaz()** - Solo Crea la Interfaz
- Crea ventana y componentes
- Configura layouts y apariencia
- Conecta eventos con métodos

### **realizarSuma()** - Solo Hace Cálculos
- Obtiene datos de la interfaz
- Realiza operaciones matemáticas
- Maneja errores de conversión
- Actualiza resultados en la interfaz

### **¿Por Qué Separar?**
- **Código más organizado** y fácil de leer
- **Fácil de modificar** cada parte independientemente
- **Fácil de probar** cada función por separado
- **Reutilizable** - puedes usar realizarSuma() desde otros lugares

---

## 🧪 **Experimentación Sugerida**

### **Experimentos Básicos:**
1. **Agrega más operaciones**
   ```java
   JButton botonRestar = new JButton("RESTAR");
   JButton botonMultiplicar = new JButton("MULTIPLICAR");
   JButton botonDividir = new JButton("DIVIDIR");
   ```

2. **Agrega un botón LIMPIAR**
   ```java
   JButton botonLimpiar = new JButton("LIMPIAR");
   botonLimpiar.addActionListener(e -> {
       campoNumero1.setText("");
       campoNumero2.setText("");
       etiquetaResultado.setText("---");
   });
   ```

3. **Cambia los colores de los campos**
   ```java
   campoNumero1.setBackground(Color.LIGHT_GRAY);
   campoNumero2.setBackground(Color.LIGHT_GRAY);
   ```

### **Experimentos Avanzados:**
4. **Agrega validación para división por cero**
5. **Haz que Enter ejecute la operación**
6. **Agrega un historial de operaciones**
7. **Permite números negativos y decimales**

### **Preguntas para Investigar:**
- ¿Qué pasa si escribes letras en lugar de números?
- ¿Qué pasa si dejas un campo vacío?
- ¿Puedes usar Integer.parseInt() en lugar de Double.parseDouble()?
- ¿Qué ocurre si cambias el layout a GridLayout?

---

## ✅ **Verificación de Comprensión**

Antes de continuar, asegúrate de que puedes:

- ✅ **Crear y usar** JTextField para entrada de datos
- ✅ **Organizar componentes** usando BorderLayout
- ✅ **Convertir texto a números** y manejar errores
- ✅ **Separar la lógica** en métodos específicos
- ✅ **Usar try-catch** para manejar errores básicos
- ✅ **Formatear números** para mostrar resultados

---

## 🚀 **Siguiente Paso**

¡Excelente! Ya sabes cómo crear aplicaciones que **reciben datos del usuario** y **realizan cálculos**. Este es un gran paso hacia aplicaciones más complejas.

En el próximo tutorial del Nivel 2, aprenderemos conceptos más avanzados y crearemos aplicaciones más sofisticadas.

**Próximo:** Tutorial 05 - Campo de Texto Avanzado (Nivel 2)

---

## 🛠️ **Solución de Problemas Comunes**

### ❌ **Error: "Cannot find symbol JTextField"**
```
Solución: Agrega el import correcto:
import javax.swing.JTextField;
```

### ❌ **Error: NumberFormatException al ejecutar**
```
Solución: El usuario escribió algo que no es un número.
Asegúrate de tener el try-catch implementado.
```

### ❌ **Error: Los componentes no se organizan bien**
```
Solución: Verifica que estés usando BorderLayout correctamente:
ventana.setLayout(new BorderLayout());
ventana.add(componente, BorderLayout.NORTH);
```

### ❌ **Error: getText() devuelve null**
```
Solución: Asegúrate de que el JTextField esté inicializado:
campoNumero1 = new JTextField();
```