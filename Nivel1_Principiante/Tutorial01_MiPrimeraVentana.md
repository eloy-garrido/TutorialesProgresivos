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

/*
 * CONCEPTOS IMPORTANTES QUE ACABAS DE APRENDER:
 * 
 * 1. JFrame: Es la ventana principal de tu aplicación
 * 2. JLabel: Sirve para mostrar texto en la interfaz
 * 3. setSize(): Define el tamaño de la ventana
 * 4. setDefaultCloseOperation(): Define qué pasa al cerrar
 * 5. setLocationRelativeTo(): Posiciona la ventana
 * 6. add(): Agrega componentes a la ventana
 * 7. setVisible(): Hace visible la ventana
 * 
 * EXPERIMENTACIÓN:
 * - Cambia el título de la ventana
 * - Modifica el tamaño (prueba con 600, 400)
 * - Cambia el mensaje del JLabel
 * - ¿Qué pasa si comentas setVisible(true)?
 * - ¿Qué pasa si comentas setDefaultCloseOperation?
 */