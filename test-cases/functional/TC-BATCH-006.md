# TC-BATCH-006 - Aceptación de importe mínimo válido

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` acepte un movimiento bancario cuyo importe sea igual al mínimo permitido de 0,01, siempre que los demás campos cumplan con las reglas de validación.

## 2. Diseño del registro de entrada

El programa recibirá un archivo secuencial QSAM de longitud fija. Cada registro tendrá exactamente 30 posiciones.

La definición del archivo será:

- Organización: secuencial (QSAM).
- Formato de registro: `RECFM=FB`.
- Longitud lógica del registro: `LRECL=30`.
- Longitud del registro en COBOL: `PIC X(30)`.

### 2.1 Layout del registro

| Campo | Posición inicial | Posición final | Longitud | Formato COBOL | Descripción |
|---|---:|---:|---:|---|---|
| ACCOUNT-NUMBER | 1 | 10 | 10 | PIC X(10) | Número de cuenta |
| AMOUNT | 11 | 21 | 11 | PIC 9(9)V99 | Importe con dos decimales implícitos |
| TRANSACTION-DATE | 22 | 29 | 8 | PIC X(8) | Fecha en formato AAAAMMDD |
| TRANSACTION-TYPE | 30 | 30 | 1 | PIC X | Tipo de movimiento |

### 2.2 Validaciones aplicables

- `ACCOUNT-NUMBER`: debe contener exactamente 10 dígitos y existir en el maestro de cuentas ficticio.
- `AMOUNT`: debe contener exactamente 11 dígitos y ser numérico.
- `AMOUNT`: debe ser mayor que cero.
- `AMOUNT`: el rango permitido es de 0,01 a 999.999.999,99.
- `TRANSACTION-DATE`: debe tener formato AAAAMMDD y representar una fecha calendario válida.
- `TRANSACTION-TYPE`: debe contener `C` (crédito) o `D` (débito).

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000000001` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | `C` |

**Registro completo de 30 posiciones:**

`00012345670000000000120261015C`

**Interpretación del importe:** `00000000001` representa 0,01, ya que los dos decimales son implícitos.

**Precondiciones:**

- El maestro de cuentas ficticio debe estar disponible para el procesamiento.
- La cuenta `0001234567` debe existir en el maestro de cuentas.
- El importe mínimo permitido debe estar definido en 0,01.
- Los campos de fecha y tipo de movimiento deben contener valores válidos.
- Todos los campos del registro deben cumplir con sus respectivas reglas de validación.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el archivo esté definido como secuencial QSAM, con `RECFM=FB` y `LRECL=30`.
4. Verificar que el registro de entrada contenga exactamente 30 posiciones.
5. Verificar que el campo `AMOUNT` contenga 11 dígitos numéricos y represente un importe de 0,01.
6. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado y disponible para pruebas.
7. Revisar la salida de movimientos aceptados.
8. Revisar la salida de registros rechazados y los contadores del procesamiento.
9. Verificar que el movimiento haya sido aceptado y que el importe procesado corresponda a 0,01.

## 5. Resultados esperados

- El registro debe ser leído correctamente por el programa.
- La cuenta debe superar las validaciones de formato y existencia.
- El importe debe superar la validación de formato numérico.
- El programa debe identificar que el importe es igual al mínimo permitido de 0,01.
- El registro debe superar todas las reglas de validación y ser aceptado.
- El movimiento debe aparecer en el archivo de movimientos aceptados, conservando los datos de entrada.
- El registro no debe aparecer en el archivo de registros rechazados.
- La cantidad de registros leídos debe ser 1.
- La cantidad de movimientos aceptados debe ser 1.
- La cantidad de movimientos rechazados debe ser 0.
- El importe procesado debe corresponder a 0,01.
- No deben registrarse errores de validación.

## 6. Resultados obtenidos

Pendientes de ejecución.

## 7. Estado

Diseñado. No ejecutado.

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.