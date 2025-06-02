# Tutorial 03: Contador Simple - Variables y Botones

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- Cómo mantener información en variables
- Usar múltiples botones
- Actualizar texto en pantalla
- ¿Qué son las variables de instancia?

**OBJETIVO FINAL:** Crear un contador que suba y baje con botones

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial03_ContadorSimple.java`:

```java
/**
 * TUTORIAL 3: CONTADOR SIMPLE - VARIABLES Y BOTONES
 * 
 * En este tutorial aprenderemos:
 * - Cómo mantener información en variables
 * - Usar múltiples botones
 * - Actualizar texto en pantalla
 * - ¿Qué son las variables de instancia?
 * 
 * OBJETIVO: Crear un contador que suba y baje con botones
 */

import javax.swing.JFrame;
import javax.swing.JButton;
import javax.swing.JLabel;
import java.awt.GridLayout;           // Para organizar componentes en cuadrícula
import java.awt.Font;                 // Para cambiar el tamaño y tipo de letra
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

/**
 * PASO 1: AHORA USAREMOS UNA CLASE COMPLETA (NO SOLO MAIN)
 * Esto nos permite tener variables que "recuerden" información
 */
public class Tutorial03_ContadorSimple {
    
    // PASO 2: VARIABLES DE INSTANCIA
    // Estas variables "pertenecen" a la clase y mantienen información
    // A diferencia de las variables locales (dentro de métodos), 
    // estas variables "viven" mientras exista el objeto
    
    private int contador = 0;           // Esta variable guarda el número actual
    private JLabel etiquetaNumero;      // Esta variable guarda la etiqueta del número
    private JFrame ventana;             // Esta variable guarda la ventana
    
    // PASO 3: CONSTRUCTOR
    // El constructor se ejecuta cuando creamos un objeto de esta clase
    // Es como las "instrucciones de armado" de nuestro contador
    public Tutorial03_ContadorSimple() {
        crearInterfaz();
    }
    
    // PASO 4: MÉTODO PARA CREAR LA INTERFAZ
    // Separamos la creación de la interfaz en su propio método
    // Esto hace el código más organizado y fácil de leer
    private void crearInterfaz() {
        
        // PASO 5: CREAR LA VENTANA PRINCIPAL
        ventana = new JFrame("Contador Simple");
        ventana.setSize(300, 200);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setLocationRelativeTo(null);
        
        // PASO 6: CREAR UN LAYOUT (DISEÑO)
        // GridLayout organiza componentes en una cuadrícula
        // GridLayout(filas, columnas)
        // 3 filas, 1 columna = los componentes se apilan verticalmente
        ventana.setLayout(new GridLayout(3, 1));
        
        // PASO 7: CREAR LA ETIQUETA QUE MUESTRA EL NÚMERO
        etiquetaNumero = new JLabel("0", JLabel.CENTER);  // Empieza mostrando 0
        
        // PASO 8: HACER EL NÚMERO MÁS GRANDE Y VISIBLE
        // Font(nombre, estilo, tamaño)
        // Font.BOLD significa letra gruesa (negrita)
        etiquetaNumero.setFont(new Font("Arial", Font.BOLD, 36));
        
        // PASO 9: CREAR LOS BOTONES
        JButton botonSumar = new JButton("+ SUMAR");
        JButton botonRestar = new JButton("- RESTAR");
        
        // PASO 10: PROGRAMAR QUÉ HACE CADA BOTÓN
        
        // Cuando presionen "SUMAR":
        botonSumar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                // Aumentar el contador en 1
                contador = contador + 1;        // También se puede escribir: contador++;
                
                // Actualizar lo que muestra la etiqueta
                // setText() cambia el texto de la etiqueta
                // String.valueOf() convierte el número a texto
                etiquetaNumero.setText(String.valueOf(contador));
            }
        });
        
        // Cuando presionen "RESTAR":
        botonRestar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                // Disminuir el contador en 1
                contador = contador - 1;        // También se puede escribir: contador--;
                
                // Actualizar la etiqueta
                etiquetaNumero.setText(String.valueOf(contador));
            }
        });
        
        // PASO 11: AGREGAR TODOS LOS COMPONENTES A LA VENTANA
        // El orden importa: se agregan de arriba hacia abajo
        ventana.add(etiquetaNumero);    // Arriba: el número
        ventana.add(botonSumar);        // Medio: botón sumar
        ventana.add(botonRestar);       // Abajo: botón restar
        
        // PASO 12: MOSTRAR LA VENTANA
        ventana.setVisible(true);
    }
    
    // PASO 13: EL MÉTODO MAIN AHORA SOLO CREA UN OBJETO
    // En lugar de hacer todo en main, creamos un objeto de nuestra clase
    public static void main(String[] args) {
        // Esto crea un objeto Tutorial03_ContadorSimple
        // Al crearlo, automáticamente se ejecuta el constructor
        new Tutorial03_ContadorSimple();
    }
}
```

---

## 🔍 **Conceptos Importantes Que Acabas de Aprender:**

### 1. **VARIABLES DE INSTANCIA:**
```java
private int contador = 0;
private JLabel etiquetaNumero;
private JFrame ventana;
```
- Se declaran **fuera de los métodos**, dentro de la clase
- **"Recuerdan" información** mientras existe el objeto
- Se pueden usar en **cualquier método** de la clase

### 2. **CONSTRUCTOR:**
```java
public Tutorial03_ContadorSimple() {
    crearInterfaz();
}
```
- Método especial que se ejecuta **al crear un objeto**
- Tiene el **mismo nombre que la clase**
- Se usa para **inicializar el objeto**

### 3. **MÉTODOS PRIVADOS:**
```java
private void crearInterfaz() {
    // código aquí
}
```
- `crearInterfaz()` es **private** (privado)
- Solo se puede usar **dentro de esta clase**
- Ayuda a **organizar el código**

### 4. **GRIDLAYOUT:**
```java
ventana.setLayout(new GridLayout(3, 1));
```
- Organiza componentes en **cuadrícula**
- `GridLayout(filas, columnas)`
- Los componentes se agregan **en orden**

### 5. **FONT:**
```java
etiquetaNumero.setFont(new Font("Arial", Font.BOLD, 36));
```
- Cambia la **apariencia del texto**
- `Font(nombre, estilo, tamaño)`
- **Estilos disponibles:** Font.BOLD, Font.ITALIC, Font.PLAIN

### 6. **setText():**
```java
etiquetaNumero.setText(String.valueOf(contador));
```
- **Cambia el texto** de un JLabel
- `String.valueOf()` **convierte números a texto**

---

## 🎮 **Flujo del Programa:**

1. **Se ejecuta main()** → Crea un objeto Tutorial03_ContadorSimple
2. **Se ejecuta el constructor** → Llama a crearInterfaz()
3. **Se crea la ventana** con todos sus componentes
4. **El programa queda "esperando"** eventos del usuario
5. **Usuario presiona un botón** → Se ejecuta el código correspondiente
6. **Se actualiza el contador** → Se muestra el nuevo valor

---

## 🧪 **Experimentación Sugerida:**

### Experimentos Básicos:
1. **Agregar un botón "REINICIAR"** que ponga el contador en 0
2. **Cambiar el incremento:** Haz que el botón sumar agregue 5 en lugar de 1
3. **Cambiar colores:** `etiquetaNumero.setForeground(Color.RED)`
4. **Agregar más botones:** Un botón que multiplique por 2

### Experimentos Avanzados:
5. **Cambiar el layout:** Prueba con `new GridLayout(1, 3)` (1 fila, 3 columnas)
6. **Agregar límites:** No permitir que el contador baje de 0
7. **Cambiar fuentes:** Prueba con diferentes nombres y tamaños
8. **Agregar un botón de "+10"** y otro de "-10"

### Preguntas para Investigar:
- ¿Qué pasa si haces `contador = contador + 10`?
- ¿Qué pasa si cambias el tamaño de la fuente a 100?
- ¿Qué ocurre si eliminas `setVisible(true)`?

---

## ✅ **Verificación de Comprensión**

Antes de continuar, asegúrate de que puedes:

- ✅ **Explicar** qué son las variables de instancia
- ✅ **Crear** un constructor básico
- ✅ **Usar** GridLayout para organizar componentes
- ✅ **Cambiar** el texto de un JLabel dinámicamente
- ✅ **Agregar** ActionListener a múltiples botones
- ✅ **Entender** por qué usamos métodos privados

---

## 🚀 **Siguiente Paso**

¡Excelente trabajo! Ya sabes cómo crear aplicaciones que **recuerden información** y **respondan a múltiples botones**.

En el próximo tutorial aprenderemos a **obtener texto del usuario** con JTextField, lo que nos permitirá crear aplicaciones mucho más interactivas.

**Próximo:** Tutorial 04 - Entrada de Datos con JTextField