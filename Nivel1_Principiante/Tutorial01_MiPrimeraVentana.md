# Tutorial 01: Mi Primera Ventana en Java Swing

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- ¿Qué es Swing?
- Crear nuestra primera ventana
- Mostrar un mensaje simple
- Conceptos básicos: JFrame y JLabel

**OBJETIVO FINAL:** Crear una ventana que muestre "¡Hola Mundo!"

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial01_MiPrimeraVentana.java`:

```java
/**
 * TUTORIAL 1: MI PRIMERA VENTANA EN JAVA SWING
 * 
 * En este tutorial aprenderemos:
 * - ¿Qué es Swing?
 * - Crear nuestra primera ventana
 * - Mostrar un mensaje simple
 * - Conceptos básicos: JFrame y JLabel
 * 
 * OBJETIVO: Crear una ventana que muestre "¡Hola Mundo!"
 */

// PASO 1: IMPORTAR LAS CLASES NECESARIAS
// Estas son clases que Java ya tiene preparadas para crear ventanas
import javax.swing.JFrame;    // Para crear la ventana principal
import javax.swing.JLabel;    // Para mostrar texto en la ventana

/**
 * PASO 2: CREAR NUESTRA CLASE
 * Una clase es como un "molde" para crear objetos
 * En este caso, vamos a crear una clase para nuestra ventana
 */
public class Tutorial01_MiPrimeraVentana {
    
    /**
     * PASO 3: EL MÉTODO MAIN
     * Este es el punto de entrada de nuestro programa
     * Cuando ejecutamos el programa, Java busca este método primero
     */
    public static void main(String[] args) {
        
        // PASO 4: CREAR LA VENTANA PRINCIPAL (JFrame)
        // JFrame es como el "marco" de nuestra ventana
        // Entre paréntesis ponemos el título que aparecerá en la barra superior
        JFrame ventana = new JFrame("Mi Primera Ventana en Java");
        
        // PASO 5: CONFIGURAR EL TAMAÑO DE LA VENTANA
        // setSize(ancho, alto) - los números están en píxeles
        // 400 píxeles de ancho y 300 píxeles de alto
        ventana.setSize(400, 300);
        
        // PASO 6: ¿QUÉ PASA CUANDO EL USUARIO CIERRA LA VENTANA?
        // Sin esta línea, aunque cerremos la ventana, el programa seguirá ejecutándose
        // EXIT_ON_CLOSE significa: "cuando cierren la ventana, termina el programa"
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        // PASO 7: CENTRAR LA VENTANA EN LA PANTALLA
        // null significa "centrar en la pantalla"
        // Sin esto, la ventana aparecería en la esquina superior izquierda
        ventana.setLocationRelativeTo(null);
        
        // PASO 8: CREAR EL TEXTO QUE QUEREMOS MOSTRAR (JLabel)
        // JLabel es un componente para mostrar texto
        // JLabel.CENTER significa que el texto estará centrado
        JLabel mensaje = new JLabel("¡Hola Mundo! Esta es mi primera ventana en Java", JLabel.CENTER);
        
        // PASO 9: AGREGAR EL TEXTO A LA VENTANA
        // La ventana está vacía, necesitamos agregarle nuestro mensaje
        ventana.add(mensaje);
        
        // PASO 10: HACER VISIBLE LA VENTANA
        // ¡IMPORTANTE! Sin esta línea, la ventana existe pero no se ve
        // Es como construir una casa pero no encender las luces
        ventana.setVisible(true);
        
        // ¡FELICIDADES! Has creado tu primera ventana en Java
        // Ejecuta este programa y verás tu ventana aparecer
    }
}
```

---

## 🔍 **Conceptos Importantes Que Acabas de Aprender:**

### 1. **JFrame** - La Ventana Principal
```java
JFrame ventana = new JFrame("Mi Primera Ventana en Java");
```
- **JFrame** es la ventana principal de tu aplicación
- Es como el "marco" donde van todos los demás componentes
- El texto entre paréntesis es el **título** que aparece en la barra superior

### 2. **JLabel** - Para Mostrar Texto
```java
JLabel mensaje = new JLabel("¡Hola Mundo!", JLabel.CENTER);
```
- **JLabel** sirve para mostrar texto en la interfaz
- `JLabel.CENTER` hace que el texto aparezca centrado
- También puede mostrar imágenes

### 3. **Configuraciones Esenciales:**

#### **setSize()** - Tamaño de la Ventana
```java
ventana.setSize(400, 300);  // ancho: 400px, alto: 300px
```

#### **setDefaultCloseOperation()** - ¿Qué Pasa al Cerrar?
```java
ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```
- **EXIT_ON_CLOSE**: Termina el programa al cerrar
- Sin esto, aunque cierres la ventana, el programa seguirá ejecutándose

#### **setLocationRelativeTo()** - Posición de la Ventana
```java
ventana.setLocationRelativeTo(null);  // null = centrar en pantalla
```

#### **add()** - Agregar Componentes
```java
ventana.add(mensaje);
```
- Agrega componentes (como texto, botones) a la ventana

#### **setVisible()** - Hacer Visible la Ventana
```java
ventana.setVisible(true);
```
- **¡CRÍTICO!** Sin esto, la ventana existe pero no se ve

---

## 🎮 **¿Cómo Funciona Este Código?**

### **Flujo de Ejecución:**
1. **Java ejecuta main()** - Punto de entrada del programa
2. **Se crea la ventana** - `new JFrame()`
3. **Se configura la ventana** - tamaño, cierre, posición
4. **Se crea el mensaje** - `new JLabel()`
5. **Se agrega el mensaje a la ventana** - `ventana.add()`
6. **Se hace visible la ventana** - `setVisible(true)`
7. **El programa queda "vivo"** esperando que el usuario interactúe

### **Conceptos Clave:**
- **Import:** Traer clases que necesitamos (`javax.swing.*`)
- **Objeto:** Cada ventana es un "objeto" creado a partir de la clase JFrame
- **Método:** Las acciones como `setSize()` son métodos que modifican el objeto
- **Parámetros:** Los valores entre paréntesis que necesita cada método

---

## 🧪 **Experimentación Sugerida**

### **Experimentos Básicos:**
1. **Cambia el título de la ventana**
   ```java
   JFrame ventana = new JFrame("¡Mi Aplicación Genial!");
   ```

2. **Modifica el tamaño** (prueba con diferentes números)
   ```java
   ventana.setSize(600, 400);  // Más grande
   ventana.setSize(200, 150);  // Más pequeño
   ```

3. **Cambia el mensaje del JLabel**
   ```java
   JLabel mensaje = new JLabel("¡Bienvenido a mi programa!", JLabel.CENTER);
   ```

### **Experimentos Avanzados:**
4. **¿Qué pasa si comentas `setVisible(true)`?**
   ```java
   // ventana.setVisible(true);  // Comenta esta línea
   ```

5. **¿Qué pasa si comentas `setDefaultCloseOperation()`?**
   ```java
   // ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
   ```

6. **Cambia la alineación del texto:**
   ```java
   JLabel mensaje = new JLabel("Texto a la izquierda", JLabel.LEFT);
   JLabel mensaje = new JLabel("Texto a la derecha", JLabel.RIGHT);
   ```

### **Preguntas para Investigar:**
- ¿Qué ocurre si no usas `setLocationRelativeTo(null)`?
- ¿Puedes hacer la ventana más grande que tu pantalla?
- ¿Qué pasa si usas números negativos en `setSize()`?

---

## ✅ **Verificación de Comprensión**

Antes de continuar al siguiente tutorial, asegúrate de que:

- ✅ **Entiendes** qué es un JFrame y para qué sirve
- ✅ **Puedes explicar** qué hace cada línea del código
- ✅ **Sabes** por qué es importante `setVisible(true)`
- ✅ **Comprendes** la diferencia entre crear un objeto y configurarlo
- ✅ **Has experimentado** con diferentes tamaños y mensajes

---

## 🚀 **Siguiente Paso**

¡Felicidades! Acabas de crear tu primera interfaz gráfica en Java. Has aprendido los conceptos fundamentales que necesitarás para todos los tutoriales siguientes.

En el próximo tutorial aprenderemos a crear **botones** y hacer que respondan cuando el usuario los presiona. ¡Las cosas se pondrán más interactivas!

**Próximo:** Tutorial 02 - Mi Primer Botón y Eventos

---

## 🛠️ **Solución de Problemas Comunes**

### ❌ **Error: "No se puede encontrar JFrame"**
```
Solución: Verifica que tengas el import correcto:
import javax.swing.JFrame;
```

### ❌ **Error: "Clase pública debe estar en archivo con mismo nombre"**
```
Solución: El archivo debe llamarse Tutorial01_MiPrimeraVentana.java
(mismo nombre que la clase)
```

### ❌ **Error: La ventana no aparece**
```
Solución: Asegúrate de que tienes setVisible(true) al final
```

### ❌ **Error: El programa no termina al cerrar la ventana**
```
Solución: Agrega setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE)
```