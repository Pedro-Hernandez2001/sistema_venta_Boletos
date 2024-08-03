# Sistema de venta de boletos de Autobuses

### Descripción
Este proyecto esta basado en el modelo `MVC`: consiste en un sistema de venta de boletos de autobús que cuenta con dos roles principales: gerente y cajero. El gerente puede agregar, eliminar, buscar y modificar cajeros, además de dar de alta autobuses, choferes y crear rutas de viaje. El sistema valida que no se permita el cruce de horarios para un mismo día si un autobús y chofer ya están asignados.
Cuando el gerente registra a un cajero, el sistema toma automáticamente el correo registrado, genera una contraseña aleatoria de 8 dígitos, la guarda en la base de datos y envía estas credenciales por correo electrónico al cajero.
El rol de cajero permite realizar ventas de boletos, teniendo acceso solo a las rutas disponibles que aún no han salido. Al realizar una venta, el cajero captura los datos del cliente (nombre, apellidos, correo, teléfono), genera un número de boleto aleatorio, asigna un número de asiento, registra el precio, destino, fecha y hora de salida. Estos datos se traspasan en un PDF y se envía automáticamente al cliente por correo electrónico.

### Usos


### Características
1.- Generación automática de contraseñas aleatorias de 8 dígitos para los cajeros
2.- Envío de credenciales por correo electrónico al registrar un nuevo cajero
Validación de horarios para evitar cruces de rutas en un mismo día para un autobús y chofer
Generación de PDF con los datos de la venta para el cliente
Roles de gerente y cajero con funcionalidades específicas para cada uno

### Requisitos
Java Development Kit (JDK)
Apache NetBeans IDE
MySQL para la base de datos
Conector JDBC de MySQL (mysql-connector-java*.jar)
Librería JavaMail para enviar emails (javamail-1.4.7.jar)
Librería JCalendar para el selector de fechas (jcalendar-1.4.jar

### Campos
| Tipo    | Campo         | Descripción                          |
|---------|---------------|--------------------------------------|
| String  | nombre        | Nombre del cliente, cajero            |
| String  | apellidos     | Apellidos del cliente,Cajero           |
| String  | correo        | Correo electrónico del cliente, cajero       |
| String  | telefono      | Teléfono del cliente, cajero                 |
| String  | numeroBoleto  | Número de boleto generado aleatoriamente |
| int     | numeroAsiento | Número de asiento asignado al cliente |
| double  | precio        | Precio del boleto                    |
| String  | destino       | Destino del viaje                    |
| Date    | fechaSalida   | Fecha de salida del viaje            |
| Time    | horaSalida    | Hora de salida del viaje             |


### Métodos
Estos son solo algunos de los metodos principales con lo que cuneta el sistema en general

| Nombre               | Tipo de Dato que Retorna | Tipo de Dato que Recibe                          | Descripción                                                                                         |
|----------------------|--------------------------|--------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| validarNombreApellidos | boolean                  | String nombre, String apellidos                  | Verifica que el nombre y apellidos del cliente no contengan números ni caracteres especiales.        |
| validarCorreo        | boolean                  | String correo                                    | Verifica que el correo electrónico del cliente tenga un formato válido.                              |
| validarTelefono      | boolean                  | String telefono                                  | Verifica que el número de teléfono del cliente tenga 10 dígitos.                                    |
| generarNumeroBoleto  | String                   | void                                             | Genera un número de boleto aleatorio de 8 dígitos.                                                   |
| asignarNumeroAsiento | int                      | int numeroAsientos                               | Asigna un número de asiento válido y disponible, considerando el total de asientos del autobús.      |
| validarPrecio        | boolean                  | double precio                                    | Verifica que el precio del boleto sea un valor numérico positivo.                                    |
| validarDestino       | boolean                  | String destino                                   | Verifica que el destino del viaje no esté vacío y no contenga caracteres especiales.                |
| validarFechaSalida   | boolean                  | Date fechaSalida                                 | Verifica que la fecha de salida sea posterior a la fecha actual.                                    |
| validarHoraSalida    | boolean                  | Time horaSalida                                  | Verifica que la hora de salida esté dentro del rango válido (00:00 a 23:59).                         |
| validarCrucesHorarios| boolean                  | Date fecha, Time horaSalida, int idAutobus, int idChofer | Verifica que no haya cruces de horarios para un autobús y chofer en una fecha específica.            |


# Instalación


```
noVisual validar = new noVisual();
        String tarjeta = txtTarjeta.getText();
        boolean valitarjeta = validar.validacionTarjetas(tarjeta);

        if (valitarjeta) {
            JOptionPane.showMessageDialog(null, "Tarjeta valida");
        } else {
            JOptionPane.showMessageDialog(null, "Tarjeta invalida");
        }
````


