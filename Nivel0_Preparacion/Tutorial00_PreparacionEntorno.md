# Tutorial 00: Preparación del Entorno - Java + VSCode

## 🎯 Objetivos de Este Tutorial

En este tutorial aprenderás:
- Instalar Java Development Kit (JDK)
- Instalar y configurar Visual Studio Code
- **Entender qué es PATH y JAVA_HOME** (explicación detallada)
- Crear tu primer proyecto Java
- Conceptos fundamentales que debes dominar antes de Swing

**OBJETIVO FINAL:** Tener el entorno completamente preparado para programar en Java

---
## 📋 PARTE 0: INSTALACIÓN de GIT
1. Instala GIT desde [ Instala GIT desde [URL_ADDRESS Instala GIT desde [URL_ADDRESS-scm.com/downloads](URL_ADDRESSwnloads](https://git-scm.com/downloads)
2. Sigue las instrucciones de instalación por defecto
3. **MUY IMPORTANTE:** Durante la instalación, marca la opción **"Add to PATH"**
4. Verifica la instalación:
   - Abre una terminal/símbolo del sistema
   - Escribe `git --version`
   - Deberías ver algo como:
   git version 2.48.1.windows.1

---

## 📋 PARTE 0.1: CLONAR REPOSITORIO DESDE GITHUB

1. Abre una terminal/símbolo del sistema
2. Navega a la carpeta donde deseas clonar el repositorio
3. Ejecuta el siguiente comando:
   ```bash
   git clone https://github.com/eloy-garrido/TutorialesProgresivos.git
   ```
4. Verifica la clonación:
   - Navega a la carpeta donde clonaste el repositorio
   - Deberías ver una carpeta llamada `TutorialesProgresivos`

---
## 📋 PARTE 1: INSTALACIÓN DEL SOFTWARE NECESARIO

### PASO 1: Instalar Java Development Kit (JDK)

#### ¿Qué es el JDK?
- **JDK** = Java Development Kit (Kit de Desarrollo Java)
- Contiene todas las herramientas para compilar y ejecutar programas Java
- Sin esto, no puedes programar en Java

#### Instrucciones de Instalación:

1. Ve a: [https://adoptium.net/](https://adoptium.net/) (recomendado - es gratis y confiable)
2. Descarga la versión **LTS más reciente** (Long Term Support)
   - Al momento de escribir esto: **Java 17** o **Java 21**
3. Ejecuta el instalador y sigue las instrucciones
4. **MUY IMPORTANTE:** Durante la instalación, marca la opción **"Add to PATH"**

#### ⚠️ ¿Qué significa "Add to PATH"? (IMPORTANTE)

**PATH** es una lista de carpetas que tu sistema operativo revisa cuando escribes un comando. 

**Ejemplo sin PATH configurado:**
```
C:\> java --version
'java' is not recognized as an internal or external command
```

**Con PATH configurado correctamente:**
```
C:\> java --version
openjdk 17.0.8 2023-07-18
```

**¿Por qué es importante?**
- Sin PATH: tendrías que escribir la ruta completa siempre: `C:\Program Files\Java\jdk-17\bin\java --version`
- Con PATH: solo escribes `java --version` desde cualquier carpeta

#### Verificar la Instalación:

1. **Abre una terminal/símbolo del sistema:**
   - **Windows:** Presiona `Win + R`, escribe `cmd`, presiona Enter
   - **Mac:** Presiona `Cmd + Espacio`, escribe `terminal`
   - **Linux:** Presiona `Ctrl + Alt + T`

2. **Verifica Java Runtime:**
   ```bash
   java --version
   ```
   Deberías ver algo como:
   ```
   openjdk 17.0.8 2023-07-18
   OpenJDK Runtime Environment (build 17.0.8+7)
   ```

3. **Verifica Java Compiler:**
   ```bash
   javac --version
   ```
   Deberías ver algo como:
   ```
   javac 17.0.8
   ```

#### 🚨 Si No Funciona - Solución de Problemas:

**Problema 1:** `'java' is not recognized`
- **Causa:** PATH no está configurado
- **Solución Windows:**
  1. Busca "Variables de entorno" en el menú de inicio
  2. Haz clic en "Editar las variables de entorno del sistema"
  3. Haz clic en "Variables de entorno"
  4. En "Variables del sistema", busca "Path"
  5. Haz clic en "Editar"
  6. Haz clic en "Nuevo"
  7. Agrega: `C:\Program Files\Eclipse Adoptium\jdk-17.0.8.101-hotspot\bin`
  8. (Ajusta la ruta según tu instalación)

**Problema 2:** "JAVA_HOME not set"
- **¿Qué es JAVA_HOME?** Es una variable que apunta a la carpeta donde está instalado Java
- **¿Por qué es importante?** Muchas herramientas (como IDEs) la necesitan para encontrar Java

**Configurar JAVA_HOME en Windows:**
1. Mismos pasos que PATH hasta "Variables de entorno"
2. En "Variables del sistema", haz clic en "Nueva"
3. Nombre: `JAVA_HOME`
4. Valor: `C:\Program Files\Eclipse Adoptium\jdk-17.0.8.101-hotspot`
5. (Sin el `\bin` al final)

**Verificar JAVA_HOME:**
```bash
echo %JAVA_HOME%
```
Debería mostrar la ruta de instalación.

---

### PASO 2: Instalar Visual Studio Code

#### ¿Por qué VSCode?
- **Gratuito** y muy popular
- **Excelente soporte** para Java
- **Fácil de usar** para principiantes
- **Muchas extensiones** útiles

#### Instrucciones:
1. Ve a: [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Descarga la versión para tu sistema operativo
3. Instala siguiendo las instrucciones por defecto

---

### PASO 3: Instalar Extensiones de Java para VSCode

#### Extensiones Esenciales:

**"Extension Pack for Java" (Microsoft)**
- Incluye todo lo necesario para Java
- Sintaxis highlighting, debugging, etc.

#### Cómo Instalar:
1. Abre VSCode
2. Ve al icono de **extensiones** (cuatro cuadrados) en la barra lateral izquierda
3. Busca **"Extension Pack for Java"**
4. Haz clic en **"Install"**
5. **Reinicia VSCode**

#### Verificar que funcionó:
- Después de reiniciar, deberías ver el ícono de Java en la barra lateral
- Si creas un archivo `.java`, debería tener colores de sintaxis

---

## 🏗️ PARTE 2: CREAR TU PRIMER PROYECTO JAVA

### PASO 4: Crear un Nuevo Proyecto Java en VSCode

#### Método Recomendado:
1. Abre VSCode
2. Presiona **Ctrl+Shift+P** (Cmd+Shift+P en Mac) - esto abre la "paleta de comandos"
3. Escribe **"Java: Create Java Project"**
4. Selecciona **"No build tools"** (para principiantes es más simple)
5. Elige una carpeta donde guardar tu proyecto
6. Dale un nombre a tu proyecto (ejemplo: "MiPrimerProyecto")

#### Estructura que se creará automáticamente:
```
MiPrimerProyecto/
├── src/                  # Aquí van tus archivos .java
├── bin/                  # Aquí van los archivos compilados (automático)
└── README.md            # Descripción del proyecto
```

---

### PASO 5: Escribir Tu Primer Programa

Dentro de la carpeta `src`, crea un archivo llamado `HolaMundo.java`:

```java
public class HolaMundo {
    public static void main(String[] args) {
        System.out.println("¡Hola Mundo!");
        System.out.println("Mi primer programa Java está funcionando");
        System.out.println("¡Estoy listo para crear interfaces gráficas!");
    }
}
```

#### Explicación del código:
- `public class HolaMundo` - Define una clase pública llamada HolaMundo
- `public static void main(String[] args)` - El punto de entrada del programa
- `System.out.println()` - Imprime texto en la consola
- **Importante:** El nombre del archivo DEBE ser igual al nombre de la clase

---

### PASO 6: Ejecutar Tu Programa

#### Opción 1: Usar VSCode (MÁS FÁCIL)
1. Con el archivo `HolaMundo.java` abierto
2. Haz clic derecho en el editor
3. Selecciona **"Run Java"**
4. ¡Deberías ver la salida en la terminal integrada!

#### Opción 2: Usar la Terminal (Para entender el proceso)
1. Abre la terminal en VSCode (Terminal → New Terminal)
2. Navega a la carpeta src: `cd src`
3. Compila: `javac HolaMundo.java`
4. Ejecuta: `java HolaMundo`

---

## 📚 PARTE 3: CONCEPTOS FUNDAMENTALES QUE DEBES DOMINAR

Antes de crear interfaces gráficas, necesitas dominar estos conceptos básicos:

### 1. Variables y Tipos de Datos

```java
public class ConceptosBasicos {
    public static void main(String[] args) {
        
        // TIPOS PRIMITIVOS (los más comunes)
        int edad = 25;              // Números enteros
        double precio = 19.99;      // Números decimales
        boolean activo = true;      // Verdadero o falso
        char inicial = 'A';         // Un solo carácter
        
        // STRINGS (CADENAS DE TEXTO)
        String nombre = "Juan";     // Texto
        String apellido = "Pérez";
        
        // CONCATENACIÓN DE STRINGS
        String nombreCompleto = nombre + " " + apellido;
        System.out.println("Nombre completo: " + nombreCompleto);
        
        // OPERACIONES MATEMÁTICAS BÁSICAS
        int suma = 5 + 3;           // 8
        int resta = 10 - 4;         // 6
        int multiplicacion = 6 * 7; // 42
        int division = 20 / 5;      // 4
        int residuo = 17 % 5;       // 2 (módulo o resto)
        
        System.out.println("Suma: " + suma);
        System.out.println("División: " + division);
    }
}
```

### 2. Estructuras de Control

```java
class EstructurasControl {
    public static void main(String[] args) {
        
        // IF-ELSE (CONDICIONALES)
        int numero = 10;
        
        if (numero > 0) {
            System.out.println("El número es positivo");
        } else if (numero < 0) {
            System.out.println("El número es negativo");
        } else {
            System.out.println("El número es cero");
        }
        
        // SWITCH (SELECCIÓN MÚLTIPLE)
        int dia = 3;
        String nombreDia;
        
        switch (dia) {
            case 1:
                nombreDia = "Lunes";
                break;
            case 2:
                nombreDia = "Martes";
                break;
            case 3:
                nombreDia = "Miércoles";
                break;
            default:
                nombreDia = "Día no válido";
        }
        
        System.out.println("Hoy es: " + nombreDia);
        
        // BUCLES (REPETICIÓN)
        
        // FOR - cuando sabes cuántas veces repetir
        System.out.println("Contando del 1 al 5:");
        for (int i = 1; i <= 5; i++) {
            System.out.println("Número: " + i);
        }
        
        // WHILE - mientras una condición sea verdadera
        int contador = 0;
        while (contador < 3) {
            System.out.println("Contador: " + contador);
            contador++; // Incrementar en 1
        }
    }
}
```

### 3. Métodos (Funciones)

```java
class EjemplosMetodos {
    
    // MÉTODO QUE NO DEVUELVE NADA (void)
    public static void saludar() {
        System.out.println("¡Hola desde un método!");
    }
    
    // MÉTODO QUE RECIBE PARÁMETROS
    public static void saludarPersona(String nombre) {
        System.out.println("¡Hola, " + nombre + "!");
    }
    
    // MÉTODO QUE DEVUELVE UN VALOR
    public static int sumar(int a, int b) {
        return a + b;
    }
    
    // MÉTODO QUE VALIDA SI UN NÚMERO ES PAR
    public static boolean esPar(int numero) {
        return numero % 2 == 0;
    }
    
    public static void main(String[] args) {
        // LLAMAR A LOS MÉTODOS
        saludar();
        saludarPersona("María");
        
        int resultado = sumar(5, 3);
        System.out.println("5 + 3 = " + resultado);
        
        boolean par = esPar(8);
        System.out.println("¿8 es par? " + par);
    }
}
```

---

## 🧪 EJERCICIOS DE PRÁCTICA

### Ejercicio 1: Calculadora Simple
Crea un programa que:
1. Pida dos números al usuario
2. Muestre el resultado de suma, resta, multiplicación y división

**Pista:**
```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
System.out.print("Ingresa un número: ");
int numero = scanner.nextInt();
```

### Ejercicio 2: Conversor de Temperaturas
Crea métodos para:
1. Convertir Celsius a Fahrenheit: `F = (C * 9/5) + 32`
2. Convertir Fahrenheit a Celsius: `C = (F - 32) * 5/9`

---

## ✅ VERIFICACIÓN FINAL

### Checklist antes de continuar con Swing:

- ✅ Java JDK instalado y funcionando (`java --version` funciona)
- ✅ PATH configurado correctamente
- ✅ JAVA_HOME configurado (opcional pero recomendado)
- ✅ VSCode instalado con Extension Pack for Java
- ✅ Puedes crear y ejecutar programas Java básicos
- ✅ Entiendes variables, if/else, bucles y métodos
- ✅ Puedes usar Scanner para entrada del usuario

### Si algo no funciona:
1. **Reinicia tu computadora** después de instalar Java
2. **Verifica las variables de entorno** PATH y JAVA_HOME
3. **Reinstala la extensión** de Java en VSCode
4. **Pide ayuda** a tu instructor

---

## 🚀 ¡Siguiente Paso!

**¡Felicidades!** Si completaste todos los pasos y ejercicios, tienes tu entorno listo para programar.

**Próximo tutorial:** Tutorial 01 - Mi Primera Ventana en Java Swing

¡Es hora de crear tu primera interfaz gráfica! 🎉