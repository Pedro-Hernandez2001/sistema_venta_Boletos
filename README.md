# Sistema de venta de boletos de Autobuses

### Descripción


### Usos


### Características


### Requisitos


### Campos
| Tipo | Campo | Descripción |
|------|-------|-------------|
| `String` | `telefono` | contiene los numeoros para validar |
| `String` | `url` | Contiene las url para validar |
| `String` | `tarjeta` | Contiene los dígitos de las tarejtas|
| `String` | `curp` | Contiene el cur para validar |
| `String` | `nss` | Contiene el numero de seguro social para validar |

### Métodos
| Nombre | Tipo de Dato que Retorna | Tipo de dato que recibe | Descripción |
|--------|--------|-------------------------|-------------|
| `validacionTelefono` | `boolean` | `int telefono` | Verifica si el número de teléfono tiene 10 dígitos. |
| `validacionURL` | `boolean` | `String url` | Verifica si la URL tiene un formato válido. |
| `validacionTarjetas` | `boolean` | `String tarjetaCredito` | Verifica si el número de tarjeta de crédito tiene 16 dígitos. |
| `validacionCURP` | `boolean` | `String curp` | Verifica si el CURP tiene un formato válido. |
| `validacionNSS` | `boolean` | `String nss` | Verifica si el número de seguridad social tiene el formato correcto. |

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


