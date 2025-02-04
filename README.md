# Sistema de venta de boletos de Autobuses

### Descripción
Este proyecto esta basado en el modelo `MVC`: consiste en un sistema de venta de boletos de autobús que cuenta con dos roles principales: gerente y cajero. El gerente puede agregar, eliminar, buscar y modificar cajeros, además de dar de alta autobuses, choferes y crear rutas de viaje. 
El sistema valida que no se permita el cruce de horarios para un mismo día si un autobús y chofer ya están asignados.
Cuando el gerente registra a un cajero, el sistema toma automáticamente el correo registrado, genera una contraseña aleatoria de 8 dígitos, la guarda en la base de datos y envía estas credenciales por correo electrónico al cajero.

El rol de cajero permite realizar ventas de boletos, teniendo acceso solo a las rutas disponibles que aún no han salido. Al realizar una venta, el cajero captura los datos del cliente (nombre, apellidos, correo, teléfono), genera un número de boleto aleatorio, asigna un número de asiento, registra el precio, destino, fecha y hora de salida. Estos datos se traspasan en un PDF y se envía automáticamente al cliente por correo electrónico.

### Usos
#### 1. Gestión de Cajeros
Registro de Cajeros: Permite al gerente registrar nuevos cajeros, generando automáticamente credenciales de acceso seguras.
Modificación y Eliminación: El gerente puede modificar o eliminar registros de cajeros según sea necesario, asegurando un control efectivo sobre los trabajadores.

#### 2. Administración de Autobuses y Choferes
Alta de Autobuses y Choferes: Facilita la incorporación de nuevos autobuses y choferes al sistema
Asignación de Rutas: Permite asignar rutas específicas a autobuses y choferes. Evitando duplicaciones de viajes

#### 3. Creación y Gestión de Rutas
Definición de Rutas: El gerente puede crear rutas de viaje, especificando destinos, horarios y precios.
Validación de Horarios: El sistema verifica automáticamente que no haya cruces de horarios para un mismo autobús y chofer en un día determinado.

#### 4. Proceso de Venta de Boletos
Visualización de Rutas Disponibles: Los cajeros pueden ver las rutas disponibles que aún no han salido
Captura de Datos del Cliente: Permite a los cajeros ingresar los datos del cliente
Envío de Confirmaciones: Se envían automáticamente el correo electrónico con los detalles de la compra

### Características
1.- Generación automática de contraseñas aleatorias de 8 dígitos para los cajeros
2.- Envío de credenciales por correo electrónico al registrar un nuevo cajero

Validación de horarios para evitar cruces de rutas en un mismo día para un autobús y chofer

Generación de PDF con los datos de la venta para el cliente

Roles de gerente y cajero con funcionalidades específicas para cada uno


### Requisitos
Java Development Kit (JDK).

Apache NetBeans IDE.

MySQL para la base de datos.

#### `Jars`
Conector JDBC de MySQL.

Librería JavaMail para enviar emails.

iText para la generación de archivos PDF.

Librería JCalendar para el selector de fechas.

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
Estos son los metodos principales de validacion con lo que cuneta el sistema en general

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
1.- primero descargamos las carpetas, las cuales ya tieine las clases, las interfaces, los jars que utilizaremos para poder hacer que funcione correctante.


![image](https://github.com/user-attachments/assets/eb8a8881-3d23-43f7-b411-a662037f1f9b)

2. Una vez descargados, los descomprimimos y nos dirigimos a nuestro IDE (apache netbeans), una vez dentro abrimos el proyecto y esperamos a que cargen los datos
3. En la carpeta que dice libreries agregamos los jars, nos quedaria de la siguiente manera
   
![image](https://github.com/user-attachments/assets/a0ceff0c-0bb7-4660-ad4c-b485018dbafa)

4. Con respecto a la base de datos tendra que abrir su gestor e importarla, con esto acompletamos la instalación

# API
 
1. posteriormente nos dirigimos a la clase coneccion donde pondremos la contraseña de nuestro MySQL.
2. Nos direigmos a las siguinetes clases:
   ConvertidorPDF
````
  private void enviarCorreoConPDF(String rutaArchivo, String destinatario, String asunto, String cuerpo) {
        
        String host = "smtp.gmail.com"; 
        final String usuario = "";  //correo
        final String clave = ""; //contraseña

````
   GeneracionPDFCredeciales
````
  public void enviarCorreoConPDF(String rutaArchivo, String destinatario, String asunto, String cuerpo, String contrasena) {
        String host = "smtp.gmail.com";
        final String usuario = ""; //correo
        final String clave = ""; //contraseña

        Properties props = new Properties();
        props.put("mail.smtp.auth", "true");
        props.put("mail.smtp.starttls.enable", "true");
        props.put("mail.smtp.host", host);
        props.put("mail.smtp.port", "587");

````
`Nota: para que funcione el correo del remitente tiene que ser  de gmail( en caso de que sea diferente dentra que cambiar el host)`

`Nota: en el correo remitente debe habilitar la opcion de aplicaciones menos seguras`
en esas partes pondremos las credenciales de nuestro correo remitente 

3. En las siguientes clases debera cambiar las rutas para que se guarden los archivos PDF
  -AccionesBotonCajero
  -GeneracionCodigo
  -GeneracionCodigo
   
  5. Realizamos las pruebas para ver el funcionamiento adecuado

## Imagenes 

A continuación, se presentan algunas imágenes de muestra que ilustran diferentes aspectos y funcionalidades de este proyecto. Estas imágenes ayudan a proporcionar una visión clara de cómo se ve y funciona la aplicación.

### Login
![Login](https://github.com/user-attachments/assets/1084e0dc-a2cf-4236-9127-4ff1024dcf9a)

### Vista del gerente 

![Gerente](https://github.com/user-attachments/assets/664728d0-adc2-4a6a-9c76-adeaba01efd4)

### Vistas del gerente 

### Registrar Empleado
![Empleado](https://github.com/user-attachments/assets/1eb15244-e3ab-4081-b201-13472d9216c1)

### Registrar Autobus

![Autobus](https://github.com/user-attachments/assets/1f834e98-7ec1-4cc3-8ddf-1b7452bcf680)

### Registrar Viaje

![Viaje](https://github.com/user-attachments/assets/08999675-08ac-4e5d-a164-9fe81a939937)

### Tablas de Cajero, Chofer, Autobus,Viaje

![Tabala Cajero](https://github.com/user-attachments/assets/0fddb5c5-d22d-4859-b1fc-eea32637becc)

![Tabla Chofer](https://github.com/user-attachments/assets/b8f2b764-d90d-4e3a-a9b6-93d2a9cb3082)

![Tabala Autobuses](https://github.com/user-attachments/assets/ebbc7dcf-e0c1-4a09-9dfc-99a5d187fd15)

![Tabla Viajes](https://github.com/user-attachments/assets/ba66c8d7-7815-4e0e-b4ed-e0bf49b7f935)

### Vistas del Cajero 

![Cajero](https://github.com/user-attachments/assets/26dd69fb-cfb6-4f82-ac9f-2c1397d03306)

### Ver Viajes

![Ver Viajes](https://github.com/user-attachments/assets/20d2f157-b281-4567-ac7c-877268512259)

### Venta de viajes 

![Venta](https://github.com/user-attachments/assets/886f2839-5cbb-46f5-a84e-ec1030078c81)

![Asiento](https://github.com/user-attachments/assets/e74934f3-6bc4-4606-a079-4002bbbaf846)

## Autores
Estudiantes de la materia de TAP_Verano
-Hernandez Reyes Pedro de Jesus
-Ignacio Aguilar Eber Aldair 

