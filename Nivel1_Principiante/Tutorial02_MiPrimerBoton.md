# Tutorial 02: Mi Primer Botón y Eventos

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- ¿Qué es un JButton?
- ¿Qué son los eventos?
- Cómo hacer que un botón "haga algo" cuando lo presionamos
- ActionListener y ActionEvent

**OBJETIVO FINAL:** Crear una ventana con un botón que muestre un mensaje cuando lo presionamos

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial02_MiPrimerBoton.java`:

```java
/**
 * TUTORIAL 2: MI PRIMER BOTÓN Y EVENTOS
 * 
 * En este tutorial aprenderemos:
 * - ¿Qué es un JButton?
 * - ¿Qué son los eventos?
 * - Cómo hacer que un botón "haga algo" cuando lo presionamos
 * - ActionListener y ActionEvent
 * 
 * OBJETIVO: Crear una ventana con un botón que muestre un mensaje cuando lo presionamos
 */

// PASO 1: IMPORTAR LAS CLASES NECESARIAS
import javax.swing.JFrame;        // Para la ventana principal
import javax.swing.JButton;       // Para crear botones
import javax.swing.JOptionPane;   // Para mostrar mensajes emergentes
import javax.swing.JPanel;        // Para organizar componentes
import java.awt.event.ActionListener;  // Para "escuchar" cuando presionan el botón
import java.awt.event.ActionEvent;     // El "evento" que ocurre cuando presionan el botón

/**
 * PASO 2: CREAR NUESTRA CLASE
 */
public class Tutorial02_MiPrimerBoton {
    
    public static void main(String[] args) {
        
        // PASO 3: CREAR LA VENTANA (como en el tutorial anterior)
        JFrame ventana = new JFrame("Mi Primer Botón");
        ventana.setSize(300, 150);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setLocationRelativeTo(null);
        
        // PASO 4: CREAR UN BOTÓN
        // JButton es un componente que el usuario puede presionar
        // Entre paréntesis va el texto que aparecerá en el botón
        JButton miBoton = new JButton("¡Presióname!");
        
        // PASO 5: ¿QUÉ PASA CUANDO PRESIONAN EL BOTÓN?
        // Necesitamos "escuchar" cuando el usuario hace clic en el botón
        // Para esto usamos un ActionListener (oyente de acciones)
        miBoton.addActionListener(new ActionListener() {
            // PASO 6: EL MÉTODO QUE SE EJECUTA CUANDO PRESIONAN EL BOTÓN
            // Este método se llama automáticamente cuando hacen clic
            public void actionPerformed(ActionEvent e) {
                // PASO 7: MOSTRAR UN MENSAJE EMERGENTE
                // JOptionPane.showMessageDialog() muestra una ventanita con un mensaje
                // ventana es dónde aparecerá el mensaje
                // El texto es lo que queremos mostrar
                JOptionPane.showMessageDialog(ventana, "¡Hola! Presionaste el botón correctamente");
            }
        });
        
        // PASO 8: AGREGAR EL BOTÓN A LA VENTANA
        ventana.add(miBoton);
        
        // PASO 9: HACER VISIBLE LA VENTANA
        ventana.setVisible(true);
    }
}
```

---

## 🔍 **Conceptos Importantes Que Acabas de Aprender:**

### 1. **JButton** - Un Botón que el Usuario Puede Presionar
```java
JButton miBoton = new JButton("¡Presióname!");
```
- **JButton** es un componente que responde a clics del usuario
- El texto entre paréntesis aparece en el botón
- Los usuarios pueden hacer clic, presionar Enter, o usar la barra espaciadora

### 2. **ActionListener** - Un "Oyente" de Eventos
```java
miBoton.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        // Código que se ejecuta cuando presionan el botón
    }
});
```
- **ActionListener** es como un "vigilante" que espera eventos
- Se "activa" cuando ocurre una acción (como un clic)
- **addActionListener()** conecta el oyente con el botón

### 3. **ActionEvent** - El Evento que Ocurre
```java
public void actionPerformed(ActionEvent e) {
    // Este código se ejecuta automáticamente
}
```
- **ActionEvent** representa "algo que pasó" (un clic)
- **actionPerformed()** es el método que se ejecuta cuando ocurre el evento
- El parámetro `e` contiene información sobre el evento

### 4. **JOptionPane** - Mensajes Emergentes
```java
JOptionPane.showMessageDialog(ventana, "¡Hola! Presionaste el botón correctamente");
```
- **JOptionPane.showMessageDialog()** muestra una ventana pequeña con un mensaje
- Primer parámetro: ventana padre (dónde aparece)
- Segundo parámetro: el mensaje a mostrar

---

## 🎮 **¿Cómo Funciona la Programación por Eventos?**

### **Concepto Clave: "No Sabemos Cuándo, Pero Sí Qué Hacer"**

#### **El Flujo Tradicional (Secuencial):**
```
1. Paso 1
2. Paso 2  
3. Paso 3
4. Fin
```

#### **El Flujo por Eventos (Reactivo):**
```
1. Crear interfaz
2. Definir qué hacer cuando pase X
3. Esperar...
4. ¡Pasó X! → Ejecutar código correspondiente
5. Volver a esperar...
```

### **En Nuestro Ejemplo:**
1. **Creamos un botón**
2. **Le decimos:** "cuando te presionen, ejecuta este código"
3. **El programa queda esperando**
4. **Usuario presiona el botón**
5. **Java automáticamente ejecuta nuestro código**
6. **Aparece el mensaje**
7. **Volvemos a esperar más eventos**

---

## 🔧 **Anatomía del ActionListener**

### **Versión Completa (Como la Escribimos):**
```java
miBoton.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        JOptionPane.showMessageDialog(ventana, "¡Hola!");
    }
});
```

### **¿Qué Significa Cada Parte?**

#### **addActionListener()** - "Agregar un Oyente"
- Le dice al botón: "avísame cuando te presionen"

#### **new ActionListener()** - "Crear un Nuevo Oyente"
- Crea un objeto que "escucha" eventos
- Es una clase especial que solo tiene un método

#### **actionPerformed()** - "Qué Hacer Cuando Pase el Evento"
- Este método se ejecuta automáticamente
- Aquí escribes lo que quieres que ocurra

#### **ActionEvent e** - "Información del Evento"
- `e` contiene detalles sobre lo que pasó
- Por ahora no lo usamos, pero está disponible

---

## 🧪 **Experimentación Sugerida**

### **Experimentos Básicos:**
1. **Cambia el texto del botón**
   ```java
   JButton miBoton = new JButton("¡Haz clic aquí!");
   ```

2. **Cambia el mensaje que aparece**
   ```java
   JOptionPane.showMessageDialog(ventana, "¡Mensaje personalizado!");
   ```

3. **Agrega otro botón con otro mensaje**
   ```java
   JButton boton2 = new JButton("Segundo botón");
   boton2.addActionListener(new ActionListener() {
       public void actionPerformed(ActionEvent e) {
           JOptionPane.showMessageDialog(ventana, "¡Segundo mensaje!");
       }
   });
   ventana.add(boton2); // ¡Pero esto no funcionará bien!
   ```

### **Experimentos Avanzados:**
4. **¿Qué pasa si no agregas el ActionListener?**
   - Comenta todo el bloque `miBoton.addActionListener(...)`
   - El botón aparece pero no hace nada

5. **Cambia el tamaño de la ventana**
   ```java
   ventana.setSize(400, 200); // Más ancho para botones más grandes
   ```

6. **Agrega más información al mensaje**
   ```java
   JOptionPane.showMessageDialog(ventana, 
       "¡Hola!\nPresionaste el botón correctamente.\n¡Felicidades!");
   ```

### **Preguntas para Investigar:**
- ¿Qué pasa si agregas dos botones sin cambiar el layout?
- ¿Puedes hacer que el mismo botón muestre mensajes diferentes cada vez?
- ¿Qué ocurre si cierras el mensaje emergente?

---

## 📚 **Otros Tipos de Eventos Comunes**

### **Eventos de Mouse:**
```java
// Cuando el mouse entra al botón
miBoton.addMouseListener(new MouseAdapter() {
    public void mouseEntered(MouseEvent e) {
        // Código cuando el mouse está sobre el botón
    }
});
```

### **Eventos de Teclado:**
```java
// Cuando presionan una tecla
ventana.addKeyListener(new KeyAdapter() {
    public void keyPressed(KeyEvent e) {
        // Código cuando presionan una tecla
    }
});
```

**NOTA:** Estos son ejemplos avanzados. Por ahora, concéntrate en ActionListener.

---

## ✅ **Verificación de Comprensión**

Antes de continuar, asegúrate de que puedes:

- ✅ **Explicar** qué es un ActionListener y para qué sirve
- ✅ **Crear** un botón y programar su comportamiento
- ✅ **Entender** el concepto de programación por eventos
- ✅ **Usar** JOptionPane para mostrar mensajes
- ✅ **Identificar** las partes principales del ActionListener

---

## 🚀 **Siguiente Paso**

¡Excelente! Ya sabes cómo crear botones que respondan a los usuarios. Este es un concepto fundamental que usarás en todas las aplicaciones interactivas.

En el próximo tutorial aprenderemos a crear aplicaciones que **recuerden información** usando variables, y haremos un contador con múltiples botones.

**Próximo:** Tutorial 03 - Contador Simple con Variables

---

## 🛠️ **Solución de Problemas Comunes**

### ❌ **Error: "Cannot find symbol ActionListener"**
```
Solución: Asegúrate de tener los imports correctos:
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
```

### ❌ **Error: El botón no hace nada al presionarlo**
```
Solución: Verifica que hayas agregado el ActionListener:
miBoton.addActionListener(new ActionListener() { ... });
```

### ❌ **Error: "Method does not override"**
```
Solución: Asegúrate de escribir correctamente:
public void actionPerformed(ActionEvent e)
```

### ❌ **Error: El mensaje no aparece**
```
Solución: Verifica la sintaxis de JOptionPane:
JOptionPane.showMessageDialog(ventana, "Tu mensaje");
```