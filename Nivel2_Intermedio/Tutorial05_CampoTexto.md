# Tutorial 05: Mi Primer Campo de Texto - JTextField

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- ¿Qué es un JTextField?
- Cómo obtener texto que escribe el usuario
- Validación básica de entrada
- Interacción entre componentes
- Tu primera aplicación interactiva real

**OBJETIVO FINAL:** Crear una aplicación que salude personalmente al usuario

---

## 📚 Conceptos Nuevos

### ¿Qué es un JTextField?
- Es un componente que permite al usuario **escribir texto**
- Similar a una "caja de texto" en páginas web
- Muy útil para formularios y entrada de datos
- Se puede leer lo que escribió el usuario con `getText()`

### Métodos importantes:
- `getText()` - obtiene el texto que escribió el usuario
- `setText()` - cambia el texto mostrado
- `setFont()` - cambia la apariencia del texto

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial05_CampoTexto.java`:

```java
/**
 * TUTORIAL 5: MI PRIMER CAMPO DE TEXTO
 * 
 * En este tutorial aprenderemos:
 * - Usar JTextField para entrada de texto
 * - Obtener texto del usuario con getText()
 * - Validación básica de entrada
 * - Interacción entre múltiples componentes
 * 
 * OBJETIVO: Crear una aplicación que salude personalmente al usuario
 */

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class Tutorial05_CampoTexto {
    
    // PASO 1: VARIABLES DE INSTANCIA
    // Necesitamos guardar referencias a los componentes para usarlos después
    private JFrame ventana;
    private JTextField campoNombre;      // Campo donde el usuario escribe su nombre
    private JButton botonSaludar;        // Botón para activar el saludo
    private JLabel etiquetaSaludo;       // Donde aparecerá el saludo personalizado
    private JButton botonLimpiar;        // Botón para limpiar todo
    
    // PASO 2: CONSTRUCTOR
    public Tutorial05_CampoTexto() {
        crearInterfaz();
    }
    
    private void crearInterfaz() {
        
        // PASO 3: CREAR LA VENTANA PRINCIPAL
        ventana = new JFrame("Mi Primer Campo de Texto");
        ventana.setSize(400, 250);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setLocationRelativeTo(null);
        
        // PASO 4: USAR BORDERLAYOUT PARA ORGANIZAR
        // BorderLayout divide la ventana en 5 áreas: NORTH, SOUTH, EAST, WEST, CENTER
        ventana.setLayout(new BorderLayout());
        
        // PASO 5: CREAR EL PANEL SUPERIOR CON INSTRUCCIONES
        JPanel panelSuperior = new JPanel();
        JLabel instrucciones = new JLabel("¿Cómo te llamas?");
        instrucciones.setFont(new Font("Arial", Font.BOLD, 16));
        panelSuperior.add(instrucciones);
        
        // PASO 6: CREAR EL PANEL CENTRAL PARA ENTRADA DE DATOS
        JPanel panelCentral = new JPanel(new GridLayout(3, 1, 10, 10));
        // GridLayout(filas, columnas, espacio horizontal, espacio vertical)
        panelCentral.setBorder(BorderFactory.createEmptyBorder(20, 50, 20, 50));
        // createEmptyBorder(arriba, izquierda, abajo, derecha) - márgenes
        
        // PASO 7: CREAR EL CAMPO DE TEXTO
        campoNombre = new JTextField();
        campoNombre.setFont(new Font("Arial", Font.PLAIN, 14));
        campoNombre.setHorizontalAlignment(JTextField.CENTER); // Centrar el texto
        
        // PASO 8: CREAR LOS BOTONES
        botonSaludar = new JButton("¡SALUDARME!");
        botonSaludar.setFont(new Font("Arial", Font.BOLD, 14));
        botonSaludar.setBackground(new Color(0, 150, 0)); // Verde
        botonSaludar.setForeground(Color.WHITE);           // Texto blanco
        
        botonLimpiar = new JButton("LIMPIAR");
        botonLimpiar.setFont(new Font("Arial", Font.BOLD, 14));
        botonLimpiar.setBackground(new Color(200, 100, 0)); // Naranja
        botonLimpiar.setForeground(Color.WHITE);
        
        // PASO 9: PROGRAMAR LOS BOTONES
        // Cuando presionen "SALUDARME":
        botonSaludar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                saludarUsuario();
            }
        });
        
        // Cuando presionen "LIMPIAR":
        botonLimpiar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                limpiarTodo();
            }
        });
        
        // PASO 10: AGREGAR COMPONENTES AL PANEL CENTRAL
        panelCentral.add(campoNombre);
        panelCentral.add(botonSaludar);
        panelCentral.add(botonLimpiar);
        
        // PASO 11: CREAR EL PANEL INFERIOR PARA EL SALUDO
        JPanel panelInferior = new JPanel();
        etiquetaSaludo = new JLabel("Escribe tu nombre y presiona el botón", JLabel.CENTER);
        etiquetaSaludo.setFont(new Font("Arial", Font.BOLD, 14));
        etiquetaSaludo.setForeground(Color.BLUE);
        panelInferior.add(etiquetaSaludo);
        
        // PASO 12: AGREGAR PANELES A LA VENTANA
        ventana.add(panelSuperior, BorderLayout.NORTH);
        ventana.add(panelCentral, BorderLayout.CENTER);
        ventana.add(panelInferior, BorderLayout.SOUTH);
        
        // PASO 13: MOSTRAR LA VENTANA
        ventana.setVisible(true);
        
        // PASO 14: PONER EL CURSOR EN EL CAMPO DE TEXTO
        campoNombre.requestFocus(); // El usuario puede empezar a escribir inmediatamente
    }
    
    // PASO 15: MÉTODO PARA SALUDAR AL USUARIO
    private void saludarUsuario() {
        // PASO 16: OBTENER EL TEXTO QUE ESCRIBIÓ EL USUARIO
        String nombre = campoNombre.getText();
        
        // PASO 17: VALIDAR QUE NO ESTÉ VACÍO
        // trim() quita espacios al inicio y final
        if (nombre.trim().isEmpty()) {
            // Si no escribió nada, mostrar mensaje de error
            etiquetaSaludo.setText("¡Por favor escribe tu nombre!");
            etiquetaSaludo.setForeground(Color.RED);
            
            // Mostrar mensaje emergente también
            JOptionPane.showMessageDialog(ventana, 
                "No puedo saludarte si no sé tu nombre 😊", 
                "Falta información", 
                JOptionPane.WARNING_MESSAGE);
            
            // Poner el cursor de vuelta en el campo
            campoNombre.requestFocus();
            return;
        }
        
        // PASO 18: CREAR EL SALUDO PERSONALIZADO
        String saludo = "¡Hola " + nombre.trim() + "! ¡Bienvenido/a! 👋";
        
        // PASO 19: MOSTRAR EL SALUDO
        etiquetaSaludo.setText(saludo);
        etiquetaSaludo.setForeground(new Color(0, 100, 0)); // Verde oscuro
        
        // PASO 20: MENSAJE EMERGENTE DE BIENVENIDA
        JOptionPane.showMessageDialog(ventana, 
            "¡Hola " + nombre.trim() + "! Es un placer conocerte 😊", 
            "¡Bienvenido/a!", 
            JOptionPane.INFORMATION_MESSAGE);
    }
    
    // PASO 21: MÉTODO PARA LIMPIAR TODO
    private void limpiarTodo() {
        // PASO 22: LIMPIAR EL CAMPO DE TEXTO
        campoNombre.setText("");
        
        // PASO 23: RESTAURAR EL MENSAJE ORIGINAL
        etiquetaSaludo.setText("Escribe tu nombre y presiona el botón");
        etiquetaSaludo.setForeground(Color.BLUE);
        
        // PASO 24: PONER EL CURSOR DE VUELTA EN EL CAMPO
        campoNombre.requestFocus();
    }
    
    // PASO 25: MÉTODO MAIN
    public static void main(String[] args) {
        new Tutorial05_CampoTexto();
    }
}
```

---

## 🔍 **Análisis Paso a Paso**

### **Nuevos Conceptos Aprendidos:**

#### 1. **JTextField**
```java
campoNombre = new JTextField();
```
- Crea una caja donde el usuario puede escribir
- Es como los formularios de páginas web

#### 2. **getText() - Obtener texto del usuario**
```java
String nombre = campoNombre.getText();
```
- Obtiene exactamente lo que escribió el usuario
- Devuelve un String que podemos usar

#### 3. **Validación básica**
```java
if (nombre.trim().isEmpty()) {
    // Error: no escribió nada
}
```
- `trim()` quita espacios en blanco
- `isEmpty()` verifica si está vacío
- Siempre validar la entrada del usuario

#### 4. **setHorizontalAlignment()**
```java
campoNombre.setHorizontalAlignment(JTextField.CENTER);
```
- Centra el texto que escribe el usuario
- Hace que se vea más profesional

#### 5. **requestFocus()**
```java
campoNombre.requestFocus();
```
- Pone el cursor en el campo de texto
- El usuario puede empezar a escribir inmediatamente

#### 6. **BorderFactory.createEmptyBorder()**
```java
panelCentral.setBorder(BorderFactory.createEmptyBorder(20, 50, 20, 50));
```
- Agrega márgenes alrededor del panel
- (arriba, izquierda, abajo, derecha)

---

## 🎮 **Cómo Funciona el Programa**

1. **Usuario abre la aplicación** → Ve un campo de texto y botones
2. **Usuario escribe su nombre** → El texto se guarda automáticamente
3. **Usuario presiona "SALUDARME"** → Se ejecuta `saludarUsuario()`
4. **Programa obtiene el texto** → `getText()` lee lo que escribió
5. **Programa valida** → Verifica que no esté vacío
6. **Si está válido** → Muestra saludo personalizado
7. **Si está vacío** → Muestra mensaje de error
8. **Usuario puede limpiar** → Botón "LIMPIAR" restaura todo

---

## 🧪 **Experimentación Sugerida**

1. **Cambiar el saludo:**
   - Modifica el mensaje de saludo
   - Agrega emojis diferentes
   - Haz que el saludo sea más largo

2. **Agregar más validaciones:**
   - Verificar que el nombre tenga al menos 2 caracteres
   - No permitir números en el nombre
   - Convertir la primera letra a mayúscula

3. **Mejorar la interfaz:**
   - Cambiar colores de los botones
   - Modificar las fuentes
   - Agregar más texto explicativo

4. **Experimentos técnicos:**
   - ¿Qué pasa si no usas `trim()`?
   - ¿Qué pasa si eliminas `requestFocus()`?
   - Intenta cambiar el layout a GridLayout

---

## ✅ **Verificación de Comprensión**

Antes de continuar al siguiente tutorial, asegúrate de que puedes:

- ✅ Explicar qué hace `getText()`
- ✅ Crear un JTextField desde cero
- ✅ Validar que el usuario escribió algo
- ✅ Usar `trim()` para limpiar espacios
- ✅ Cambiar el color del texto de un JLabel
- ✅ Usar `requestFocus()` para mejorar la experiencia

---

## 🚀 **Siguiente Paso**

¡Felicidades! Ya dominas la entrada de texto básica. En el próximo tutorial aprenderemos a crear un juego simple de adivinanza usando todo lo que has aprendido hasta ahora.

**Próximo:** Tutorial 06 - Juego de Adivinanza Simple