# 🏦 ACTIVIDAD INTEGRADORA NIVEL 1: CAJERO AUTOMÁTICO SIMPLE

## 📋 DESCRIPCIÓN DEL PROBLEMA

¡Felicidades! Has sido contratado por un banco local para desarrollar un **simulador de cajero automático simple**. El banco necesita una aplicación que permita a los usuarios realizar operaciones básicas de consulta y transacciones con su cuenta bancaria.

### 🎯 OBJETIVO PRINCIPAL
Crear una aplicación de escritorio que simule las funciones básicas de un cajero automático, aplicando **TODOS** los conceptos aprendidos en el Nivel 1.

---

## 📊 REQUERIMIENTOS FUNCIONALES

### **FUNCIONALIDADES QUE DEBE TENER TU CAJERO:**

1. **💰 CONSULTAR SALDO**
   - Mostrar el saldo actual de la cuenta
   - El saldo inicial debe ser $1000.00

2. **💳 DEPOSITAR DINERO**
   - Permitir al usuario ingresar una cantidad a depositar
   - Validar que la cantidad sea un número positivo
   - Actualizar y mostrar el nuevo saldo

3. **💸 RETIRAR DINERO**
   - Permitir al usuario ingresar una cantidad a retirar
   - Validar que:
     - La cantidad sea un número positivo
     - No se pueda retirar más dinero del disponible
   - Actualizar y mostrar el nuevo saldo

4. **📋 MOSTRAR HISTORIAL SIMPLE**
   - Mostrar la última operación realizada
   - Ejemplo: "Última operación: Depósito de $150.00"

5. **🔄 RESETEAR CUENTA**
   - Volver el saldo a $1000.00
   - Limpiar el historial

---

## 🛠️ ESPECIFICACIONES TÉCNICAS

### **COMPONENTES QUE DEBES USAR:**

#### **📝 OBLIGATORIOS (Conceptos del Nivel 1):**
- [x] **JFrame** - Ventana principal del cajero
- [x] **JLabel** - Para mostrar información (saldo, mensajes, etc.)
- [x] **JButton** - Para las diferentes operaciones (al menos 4 botones)
- [x] **JTextField** - Para que el usuario ingrese cantidades
- [x] **ActionListener** - Para manejar eventos de botones
- [x] **Variables de instancia** - Para mantener el saldo y estado
- [x] **GridLayout o BorderLayout** - Para organizar la interfaz
- [x] **JOptionPane** - Para mostrar mensajes de confirmación/error
- [x] **try-catch** - Para manejar errores de entrada

#### **💡 FUNCIONALIDADES ESPERADAS:**
- [x] **Manejo de eventos** - Cada botón debe hacer algo específico
- [x] **Actualización dinámica** - El saldo debe actualizarse en tiempo real
- [x] **Validación de datos** - No permitir entradas inválidas
- [x] **Mensajes informativos** - Feedback claro para el usuario

---

## 🎨 DISEÑO DE LA INTERFAZ

### **SUGERENCIA DE LAYOUT:**

```
╔═══════════════════════════════════════╗
║          🏦 CAJERO AUTOMÁTICO         ║
╠═══════════════════════════════════════╣
║  Saldo actual: $1,000.00             ║
║                                       ║
║  Ingrese cantidad: [_____________]    ║
║                                       ║
║  [CONSULTAR SALDO] [DEPOSITAR]       ║
║  [RETIRAR]         [RESETEAR]        ║
║                                       ║
║  Última operación: ---               ║
╚═══════════════════════════════════════╝
```

### **ELEMENTOS CLAVE:**
- **Título claro** en la parte superior
- **Saldo visible** siempre actualizado
- **Campo de entrada** para cantidades
- **Botones organizados** de manera intuitiva
- **Área de mensajes** para feedback

---

## 📝 CASOS DE USO A PROBAR

### **🔍 CASO 1: CONSULTAR SALDO**
```
Usuario presiona "CONSULTAR SALDO"
→ Sistema muestra: "Su saldo actual es: $1,000.00"
```

### **💰 CASO 2: DEPOSITAR DINERO VÁLIDO**
```
Usuario ingresa: 250.50
Usuario presiona "DEPOSITAR"
→ Sistema actualiza saldo a: $1,250.50
→ Sistema muestra: "Depósito exitoso. Nuevo saldo: $1,250.50"
```

### **💸 CASO 3: RETIRAR DINERO VÁLIDO**
```
Usuario ingresa: 100
Usuario presiona "RETIRAR"
→ Sistema actualiza saldo a: $900.00
→ Sistema muestra: "Retiro exitoso. Nuevo saldo: $900.00"
```

### **❌ CASO 4: RETIRAR MÁS DINERO DEL DISPONIBLE**
```
Saldo actual: $500.00
Usuario ingresa: 600
Usuario presiona "RETIRAR"
→ Sistema muestra: "Error: Fondos insuficientes"
→ Saldo permanece igual
```

### **❌ CASO 5: ENTRADA INVÁLIDA**
```
Usuario ingresa: "abc" o deja vacío
Usuario presiona cualquier operación
→ Sistema muestra: "Error: Ingrese una cantidad válida"
```

---

## 💡 PISTAS Y CONSEJOS

### **🚀 PARA EMPEZAR:**
1. **Crea la estructura básica** (JFrame, variables de instancia)
2. **Agrega los componentes uno por uno** (JLabel para saldo, JTextField, botones)
3. **Implementa una operación a la vez** (empieza con "Consultar Saldo")
4. **Prueba cada funcionalidad** antes de pasar a la siguiente

### **🔧 TIPS TÉCNICOS:**
```java
// Para formatear el saldo como moneda:
String saldoFormateado = String.format("$%.2f", saldo);

// Para validar entrada positiva:
if (cantidad <= 0) {
    JOptionPane.showMessageDialog(ventana, "Ingrese una cantidad positiva");
    return;
}

// Para validar fondos suficientes:
if (cantidad > saldoActual) {
    JOptionPane.showMessageDialog(ventana, "Fondos insuficientes");
    return;
}
```

### **📚 CONCEPTOS A REPASAR:**
- **Tutorial 01**: Creación de ventana y configuración básica
- **Tutorial 02**: Botones y ActionListener
- **Tutorial 03**: Variables de instancia y múltiples botones
- **Tutorial 04**: JTextField, validación y try-catch

---

---

## 🏆 BONUS OPCIONAL (Ideas Extra)

Si terminas rápido y quieres ir más allá:

1. **🎨 Mejorar el diseño:**
   - Colores del tema bancario (azul, verde)
   - Íconos en los botones
   - Fuentes más grandes

2. **📊 Funcionalidades adicionales:**
   - Contador de transacciones realizadas
   - Límite diario de retiros
   - Diferentes tipos de cuenta

3. **🔒 Seguridad básica:**
   - PIN de 4 dígitos para acceder
   - Máximo 3 intentos fallidos

---

## ❓ PREGUNTAS FRECUENTES

### **🤔 "¿Por dónde empiezo?"**
Comienza creando una ventana simple con un JLabel que muestre "Saldo: $1000.00" y ve agregando componentes gradualmente.

### **🤔 "¿Cómo formateo el dinero?"**
Usa `String.format("$%.2f", saldo)` para mostrar el saldo con dos decimales.

### **🤔 "¿Qué pasa si el usuario ingresa letras?"**
Usa try-catch con NumberFormatException, como aprendiste en el Tutorial 4.

### **🤔 "¿Debo usar GridLayout o BorderLayout?"**
Cualquiera está bien. BorderLayout es bueno para dividir en secciones (arriba: título, centro: operaciones, abajo: mensajes).

---

## 🎉 ¡BUENA SUERTE!

Esta actividad integra **TODOS** los conceptos que aprendiste en el Nivel 1. Si puedes completarla exitosamente, significa que tienes una base sólida en Java Swing y estás listo para avanzar al Nivel 2.

**Recuerda:** No hay una única forma "correcta" de resolver este problema. Lo importante es que uses los conceptos aprendidos y que tu aplicación funcione según los requerimientos.

¡Demuestra todo lo que has aprendido! 🚀