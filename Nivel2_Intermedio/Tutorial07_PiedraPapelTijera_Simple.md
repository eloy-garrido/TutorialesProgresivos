# Tutorial 07: Piedra, Papel y Tijera - Versión Simple

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- Implementar lógica de juego real
- Usar arrays para opciones
- Comparación de strings
- Estructura de un juego completo simple

**OBJETIVO FINAL:** Crear el famoso juego Piedra, Papel y Tijera contra la computadora

---

## 🎮 Las Reglas del Juego

### **Reglas Clásicas:**
- **Piedra** vence a **Tijera** (la rompe) 🪨 ✂️
- **Papel** vence a **Piedra** (la cubre) 📄 🪨
- **Tijera** vence a **Papel** (lo corta) ✂️ 📄
- **Mismo elemento** = **Empate** 🤝

### **Cómo Jugar:**
1. **Tú eliges:** Piedra, Papel o Tijera
2. **La computadora elige** aleatoriamente
3. **Se comparan** las elecciones
4. **Se determina el ganador** según las reglas

---

## 💻 El Código Completo

Crea un archivo llamado `Tutorial07_PiedraPapelTijera_Simple.java`:

```java
/**
 * TUTORIAL 7: PIEDRA, PAPEL Y TIJERA - VERSIÓN SIMPLE
 * 
 * En este tutorial aprenderemos:
 * - Implementar lógica de juego real
 * - Usar arrays para opciones
 * - Comparación de strings
 * - Estructura de un juego completo simple
 * 
 * OBJETIVO: Crear el famoso juego Piedra, Papel y Tijera contra la computadora
 */

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.util.Random;

public class Tutorial07_PiedraPapelTijera_Simple {
    
    // PASO 1: VARIABLES DE INSTANCIA
    private JFrame ventana;
    private JLabel etiquetaEleccionJugador;
    private JLabel etiquetaEleccionComputadora;
    private JLabel etiquetaResultado;
    private JButton botonPiedra, botonPapel, botonTijera;
    private JButton botonReiniciar;
    
    // PASO 2: VARIABLES PARA LA LÓGICA DEL JUEGO
    private Random random;
    private String[] opciones = {"PIEDRA", "PAPEL", "TIJERA"};  // Array con las opciones
    // Un array es como una lista numerada: posición 0=PIEDRA, 1=PAPEL, 2=TIJERA
    
    // PASO 3: CONSTRUCTOR
    public Tutorial07_PiedraPapelTijera_Simple() {
        random = new Random();
        crearInterfaz();
    }
    
    private void crearInterfaz() {
        
        // PASO 4: CREAR LA VENTANA
        ventana = new JFrame("🎮 Piedra, Papel y Tijera 🎮");
        ventana.setSize(500, 400);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setLocationRelativeTo(null);
        ventana.setLayout(new BorderLayout());
        
        // PASO 5: PANEL SUPERIOR - TÍTULO
        JPanel panelTitulo = new JPanel();
        JLabel titulo = new JLabel("¡PIEDRA, PAPEL Y TIJERA!", JLabel.CENTER);
        titulo.setFont(new Font("Arial", Font.BOLD, 20));
        titulo.setForeground(new Color(0, 100, 200));  // Color azul personalizado
        panelTitulo.add(titulo);
        
        // PASO 6: PANEL CENTRAL - BOTONES DE ELECCIÓN
        JPanel panelBotones = new JPanel(new GridLayout(1, 3, 20, 20));
        panelBotones.setBorder(BorderFactory.createEmptyBorder(30, 30, 30, 30));
        
        // PASO 7: CREAR LOS BOTONES CON EMOJIS Y TEXTO
        botonPiedra = new JButton("<html><center>🪨<br>PIEDRA</center></html>");
        botonPapel = new JButton("<html><center>📄<br>PAPEL</center></html>");
        botonTijera = new JButton("<html><center>✂️<br>TIJERA</center></html>");
        
        // PASO 8: CONFIGURAR APARIENCIA DE LOS BOTONES
        Font fuenteBotones = new Font("Arial", Font.BOLD, 16);
        Dimension tamanoBotones = new Dimension(120, 80);
        
        configurarBoton(botonPiedra, fuenteBotones, tamanoBotones, new Color(139, 69, 19));   // Marrón
        configurarBoton(botonPapel, fuenteBotones, tamanoBotones, new Color(255, 255, 255));  // Blanco
        configurarBoton(botonTijera, fuenteBotones, tamanoBotones, new Color(192, 192, 192)); // Gris
        
        // PASO 9: AGREGAR EVENTOS A LOS BOTONES
        // Cuando presionen cada botón, llamamos a jugar() con la opción correspondiente
        botonPiedra.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                jugar("PIEDRA");
            }
        });
        
        botonPapel.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                jugar("PAPEL");
            }
        });
        
        botonTijera.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                jugar("TIJERA");
            }
        });
        
        panelBotones.add(botonPiedra);
        panelBotones.add(botonPapel);
        panelBotones.add(botonTijera);
        
        // PASO 10: PANEL INFERIOR - RESULTADOS
        JPanel panelResultados = new JPanel(new GridLayout(4, 1, 10, 10));
        panelResultados.setBorder(BorderFactory.createEmptyBorder(20, 20, 20, 20));
        
        // PASO 11: ETIQUETAS PARA MOSTRAR RESULTADOS
        etiquetaEleccionJugador = new JLabel("Tu elección: ---", JLabel.CENTER);
        etiquetaEleccionJugador.setFont(new Font("Arial", Font.BOLD, 14));
        
        etiquetaEleccionComputadora = new JLabel("Computadora: ---", JLabel.CENTER);
        etiquetaEleccionComputadora.setFont(new Font("Arial", Font.BOLD, 14));
        
        etiquetaResultado = new JLabel("¡Elige tu jugada!", JLabel.CENTER);
        etiquetaResultado.setFont(new Font("Arial", Font.BOLD, 16));
        
        // PASO 12: BOTÓN PARA REINICIAR
        botonReiniciar = new JButton("🔄 JUGAR OTRA VEZ");
        botonReiniciar.setFont(new Font("Arial", Font.BOLD, 14));
        botonReiniciar.setBackground(new Color(50, 150, 50));
        botonReiniciar.setForeground(Color.WHITE);
        botonReiniciar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                reiniciarJuego();
            }
        });
        
        panelResultados.add(etiquetaEleccionJugador);
        panelResultados.add(etiquetaEleccionComputadora);
        panelResultados.add(etiquetaResultado);
        panelResultados.add(botonReiniciar);
        
        // PASO 13: AGREGAR PANELES A LA VENTANA
        ventana.add(panelTitulo, BorderLayout.NORTH);
        ventana.add(panelBotones, BorderLayout.CENTER);
        ventana.add(panelResultados, BorderLayout.SOUTH);
        
        ventana.setVisible(true);
    }
    
    // PASO 14: MÉTODO AUXILIAR PARA CONFIGURAR BOTONES
    // Este método evita repetir código para configurar cada botón
    private void configurarBoton(JButton boton, Font fuente, Dimension tamaño, Color color) {
        boton.setFont(fuente);
        boton.setPreferredSize(tamaño);
        boton.setBackground(color);
        if (color.equals(Color.WHITE)) {
            boton.setForeground(Color.BLACK);  // Texto negro para fondo blanco
        } else {
            boton.setForeground(Color.WHITE);  // Texto blanco para otros colores
        }
        boton.setFocusPainted(false);  // Quitar el borde de foco
    }
    
    // PASO 15: MÉTODO PRINCIPAL DEL JUEGO
    private void jugar(String eleccionJugador) {
        
        // PASO 16: LA COMPUTADORA ELIGE ALEATORIAMENTE
        // random.nextInt(3) genera 0, 1, o 2
        // Usamos ese número como índice del array opciones
        int indiceComputadora = random.nextInt(3);
        String eleccionComputadora = opciones[indiceComputadora];
        
        // PASO 17: MOSTRAR LAS ELECCIONES
        etiquetaEleccionJugador.setText("Tu elección: " + agregarEmoji(eleccionJugador));
        etiquetaEleccionComputadora.setText("Computadora: " + agregarEmoji(eleccionComputadora));
        
        // PASO 18: DETERMINAR EL GANADOR
        String resultado = determinarGanador(eleccionJugador, eleccionComputadora);
        
        // PASO 19: MOSTRAR EL RESULTADO CON COLOR
        etiquetaResultado.setText(resultado);
        
        if (resultado.contains("GANASTE")) {
            etiquetaResultado.setForeground(new Color(0, 150, 0));  // Verde para victoria
        } else if (resultado.contains("PERDISTE")) {
            etiquetaResultado.setForeground(new Color(200, 0, 0));  // Rojo para derrota
        } else {
            etiquetaResultado.setForeground(new Color(200, 100, 0)); // Naranja para empate
        }
    }
    
    // PASO 20: MÉTODO PARA AGREGAR EMOJIS A LAS OPCIONES
    private String agregarEmoji(String opcion) {
        // PASO 21: USAR SWITCH PARA ASIGNAR EMOJIS
        // switch es más claro que múltiples if cuando comparamos una variable con varios valores
        switch (opcion) {
            case "PIEDRA":
                return "🪨 " + opcion;
            case "PAPEL":
                return "📄 " + opcion;
            case "TIJERA":
                return "✂️ " + opcion;
            default:
                return opcion;  // En caso de error, devolver la opción sin emoji
        }
    }
    
    // PASO 22: MÉTODO PARA DETERMINAR EL GANADOR
    private String determinarGanador(String jugador, String computadora) {
        
        // PASO 23: VERIFICAR EMPATE PRIMERO
        // Si ambos eligieron lo mismo, es empate
        if (jugador.equals(computadora)) {
            return "¡EMPATE! 🤝";
        }
        
        // PASO 24: VERIFICAR TODAS LAS CONDICIONES DE VICTORIA DEL JUGADOR
        // Piedra vence Tijera, Papel vence Piedra, Tijera vence Papel
        boolean jugadorGana = false;
        
        if (jugador.equals("PIEDRA") && computadora.equals("TIJERA")) {
            jugadorGana = true;
        } else if (jugador.equals("PAPEL") && computadora.equals("PIEDRA")) {
            jugadorGana = true;
        } else if (jugador.equals("TIJERA") && computadora.equals("PAPEL")) {
            jugadorGana = true;
        }
        
        // PASO 25: DEVOLVER EL RESULTADO APROPIADO
        if (jugadorGana) {
            return "¡GANASTE! 🎉";
        } else {
            return "¡PERDISTE! 😔";
        }
    }
    
    // PASO 26: MÉTODO PARA REINICIAR EL JUEGO
    private void reiniciarJuego() {
        etiquetaEleccionJugador.setText("Tu elección: ---");
        etiquetaEleccionComputadora.setText("Computadora: ---");
        etiquetaResultado.setText("¡Elige tu jugada!");
        etiquetaResultado.setForeground(Color.BLACK);  // Volver al color negro
    }
    
    public static void main(String[] args) {
        new Tutorial07_PiedraPapelTijera_Simple();
    }
}
```

---

## 🔍 **Conceptos Nuevos Que Acabas de Aprender:**

### 1. **Arrays (Arreglos)** - Listas de Elementos
```java
String[] opciones = {"PIEDRA", "PAPEL", "TIJERA"};
```
- **Arrays** almacenan múltiples valores del mismo tipo
- Se accede por **índice**: `opciones[0]`, `opciones[1]`, `opciones[2]`
- Los **índices empiezan en 0**
- `opciones[0]` = "PIEDRA", `opciones[1]` = "PAPEL", `opciones[2]` = "TIJERA"

### 2. **Switch Statement** - Alternativa a Múltiples if-else
```java
switch (opcion) {
    case "PIEDRA":
        return "🪨 " + opcion;
    case "PAPEL":
        return "📄 " + opcion;
    case "TIJERA":
        return "✂️ " + opcion;
    default:
        return opcion;
}
```
- **switch** es más claro que múltiples if-else
- **case** para cada valor posible
- **break** termina cada caso (aquí no es necesario porque usamos return)
- **default** para casos no contemplados

### 3. **HTML en Botones** - Texto Multilínea
```java
JButton boton = new JButton("<html><center>🪨<br>PIEDRA</center></html>");
```
- `<html>` permite usar HTML básico en componentes Swing
- `<center>` centra el texto
- `<br>` hace salto de línea
- Permite crear botones más atractivos visualmente

### 4. **Colores Personalizados** - new Color()
```java
new Color(139, 69, 19);    // Marrón (rojo, verde, azul)
new Color(0, 150, 0);      // Verde
```
- **new Color(rojo, verde, azul)** crea colores personalizados
- Valores de **0 a 255** para cada componente
- `Color.WHITE`, `Color.BLACK` son constantes predefinidas

### 5. **Métodos Auxiliares** - Organización del Código
```java
private void configurarBoton(JButton boton, Font fuente, Dimension tamaño, Color color) {
    // Configuración común para todos los botones
}
```
- **configurarBoton()** evita repetir código
- **agregarEmoji()** separa responsabilidades
- **Un método debe hacer una sola cosa bien**

### 6. **Operador .equals()** - Comparación de Strings
```java
if (jugador.equals(computadora)) {
    return "¡EMPATE!";
}
```
- **SIEMPRE** usar `.equals()` para comparar strings
- **NUNCA** uses `==` para comparar strings
- `.contains()` verifica si contiene una subcadena

### 7. **Variables Booleanas** - Clarificar Lógica
```java
boolean jugadorGana = false;
if (jugador.equals("PIEDRA") && computadora.equals("TIJERA")) {
    jugadorGana = true;
}
```
- **boolean** ayuda a clarificar lógica compleja
- Hace el código más legible y fácil de entender

---

## 🎮 **Lógica del Juego - Análisis Detallado:**

### **Tabla de Resultados:**
| Jugador | Computadora | Resultado |
|---------|-------------|-----------|
| Piedra  | Piedra      | Empate    |
| Piedra  | Papel       | Derrota   |
| Piedra  | Tijera      | Victoria  |
| Papel   | Piedra      | Victoria  |
| Papel   | Papel       | Empate    |
| Papel   | Tijera      | Derrota   |
| Tijera  | Piedra      | Derrota   |
| Tijera  | Papel       | Victoria  |
| Tijera  | Tijera      | Empate    |

### **Flujo del Programa:**
1. **Usuario hace clic** en un botón (Piedra, Papel o Tijera)
2. **Se ejecuta jugar()** con la elección del usuario
3. **La computadora elige** aleatoriamente usando el array
4. **Se muestran ambas elecciones** con emojis
5. **Se determina el ganador** usando las reglas del juego
6. **Se muestra el resultado** con color apropiado
7. **Usuario puede jugar otra vez** o reiniciar

---

## 🎨 **Detalles de Interfaz - Mejores Prácticas:**

### **Colores Temáticos:**
- **Verde** para victorias (positivo)
- **Rojo** para derrotas (negativo)  
- **Naranja** para empates (neutral)
- **Azul** para títulos (informativo)

### **Fuentes y Tamaños:**
- **Título:** Arial Bold 20px
- **Botones:** Arial Bold 16px
- **Resultados:** Arial Bold 14-16px

### **Espaciado y Márgenes:**
```java
panelBotones.setBorder(BorderFactory.createEmptyBorder(30, 30, 30, 30));
```
- **createEmptyBorder(arriba, izquierda, abajo, derecha)**
- Mejora la apariencia visual
- Evita que los componentes estén "pegados"

---

## 🧪 **Experimentación Sugerida**

### **Experimentos Básicos:**
1. **Agregar contador de puntuación**
   ```java
   private int victoriasJugador = 0;
   private int victoriasComputadora = 0;
   ```

2. **Cambiar emojis y colores**
   - Usa diferentes emojis para cada opción
   - Experimenta con otros colores

3. **Modificar el array de opciones**
   ```java
   String[] opciones = {"🪨 ROCA", "📜 PERGAMINO", "🗡️ ESPADA"};
   ```

### **Experimentos Intermedios:**
4. **Implementar "mejor de 3" o "mejor de 5"**
5. **Agregar más opciones** (Lagarto, Spock del Big Bang Theory)
6. **Historial de jugadas** - mostrar últimas 5 partidas
7. **Estadísticas** - porcentaje de victorias

### **Desafíos Avanzados:**
8. **Diferentes niveles de dificultad** de la IA
9. **Modo multijugador** (dos humanos)
10. **Guardar estadísticas** en un archivo
11. **Animaciones** simples en los botones

### **Preguntas para Investigar:**
- ¿Qué pasa si cambias el tamaño del array opciones?
- ¿Qué pasa si eliminas el `break` en el switch?
- ¿Cómo harías para que la computadora "haga trampa"?
- ¿Puedes hacer que los botones cambien de color al hacer hover?

---

## ✅ **Verificación de Comprensión**

Antes de continuar, asegúrate de que puedes:

- ✅ **Explicar** cómo funcionan los arrays y sus índices
- ✅ **Usar** switch statement correctamente
- ✅ **Implementar** lógica de juego con condiciones múltiples
- ✅ **Comparar strings** usando .equals()
- ✅ **Crear** métodos auxiliares para organizar código
- ✅ **Entender** el flujo completo del juego

---

## 🚀 **¡Felicidades! Has Completado el Nivel 2**

¡Increíble! Has creado un **juego completo y funcional** de Piedra, Papel y Tijera. Has dominado:

- **Variables de instancia** y constructores
- **Eventos** y ActionListeners  
- **Layouts** y organización visual
- **Validación** de entrada del usuario
- **Lógica de juego** y condiciones complejas
- **Arrays** y números aleatorios
- **Métodos auxiliares** y organización del código

### **Próximos Pasos:**
El **Nivel 3 (Avanzado)** incluirá:
- Aplicaciones con múltiples ventanas
- Persistencia de datos (guardar/cargar)
- Arquitectura más compleja (MVC)
- Componentes avanzados (JTable, JTree, JMenu)
- Proyectos de nivel profesional

---

## 🛠️ **Solución de Problemas Comunes**

### ❌ **Error: "Array index out of bounds"**
```
Solución: Verifica que el índice del array esté dentro del rango.
Para array de 3 elementos, usa índices 0, 1, 2.
```

### ❌ **Error: Switch statement sin break**
```
Solución: Si usas switch sin return, agrega break después de cada case.
```

### ❌ **Error: Strings no se comparan correctamente**
```
Solución: Usa .equals() en lugar de == para comparar strings.
```

### ❌ **Error: Colores no aparecen**
```
Solución: Verifica que hayas llamado a setForeground() después de setText().
```