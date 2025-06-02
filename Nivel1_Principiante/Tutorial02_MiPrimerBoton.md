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

/*
 * CONCEPTOS NUEVOS QUE ACABAS DE APRENDER:
 * 
 * 1. JButton: Un botón que el usuario puede presionar
 * 2. ActionListener: Un "oyente" que espera a que pase algo (como un clic)
 * 3. ActionEvent: El evento que ocurre cuando presionan el botón
 * 4. actionPerformed(): El método que se ejecuta cuando ocurre el evento
 * 5. JOptionPane.showMessageDialog(): Muestra mensajes emergentes
 * 6. addActionListener(): Conecta el botón con el oyente
 * 
 * ¿CÓMO FUNCIONA ESTO?
 * 
 * 1. Creamos un botón
 * 2. Le decimos al botón: "cuando te presionen, ejecuta este código"
 * 3. El usuario presiona el botón
 * 4. Java automáticamente ejecuta el código que le dijimos
 * 5. Aparece el mensaje
 * 
 * ESTO SE LLAMA "PROGRAMACIÓN POR EVENTOS"
 * - No sabemos CUÁNDO el usuario presionará el botón
 * - Pero sí sabemos QUÉ hacer cuando lo presione
 * - Java se encarga de "avisar" cuando ocurre el evento
 * 
 * EXPERIMENTACIÓN:
 * - Cambia el texto del botón
 * - Cambia el mensaje que aparece
 * - Agrega otro botón con otro mensaje
 * - ¿Qué pasa si no agregas el ActionListener?
 */