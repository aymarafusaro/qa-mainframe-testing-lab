# TC-BATCH-004 - Rechazo por cuenta con caracteres no numéricos

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento bancario cuya cuenta contiene caracteres no numéricos, aunque la longitud del campo sea correcta y los demás datos cumplan con las reglas de validación.

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

- `ACCOUNT-NUMBER`: debe contener exactamente 10 caracteres numéricos.
- `ACCOUNT-NUMBER`: no debe contener letras, espacios ni otros caracteres no numéricos.
- Validación de formato: debe realizarse antes de consultar la existencia de la cuenta en el maestro ficticio.
- `AMOUNT`: debe contener exactamente 11 dígitos y ser numérico.
- `AMOUNT`: debe ser mayor que cero.
- `TRANSACTION-DATE`: debe tener formato AAAAMMDD y representar una fecha calendario válida.
- `TRANSACTION-TYPE`: debe contener `C` (crédito) o `D` (débito).

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `00012A4567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | `C` |

**Registro completo de 30 posiciones:**

`00012A45670000012505020261015C`

**Interpretación del importe:** `00000125050` representa 1.250,50, ya que los dos decimales son implícitos.

**Precondiciones:**

- El archivo de entrada debe estar disponible para el procesamiento.
- Los demás campos del registro deben cumplir con sus respectivas reglas de validación.
- La cuenta debe ser rechazada por su contenido no numérico, independientemente de su existencia o inexistencia en el maestro ficticio.

## 4. Pasos de prueba

1. Preparar el archivo de entrada con el registro definido en este caso.
2. Verificar que el archivo esté definido como secuencial QSAM, con `RECFM=FB` y `LRECL=30`.
3. Verificar que el registro de entrada contenga exactamente 30 posiciones.
4. Verificar que `ACCOUNT-NUMBER` contenga 10 caracteres y que incluya la letra `A` en la posición correspondiente.
5. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado y disponible para pruebas.
6. Revisar la salida de movimientos aceptados.
7. Revisar la salida de registros rechazados y los contadores del procesamiento.
8. Verificar que el motivo de rechazo corresponda al formato no numérico de `ACCOUNT-NUMBER`.

## 5. Resultados esperados

- El registro debe ser leído correctamente por el programa.
- El programa debe identificar que `ACCOUNT-NUMBER` contiene un carácter no numérico.
- El registro debe ser rechazado por formato inválido de cuenta.
- La validación de formato debe impedir que el registro avance a la consulta de existencia en el maestro de cuentas.
- El registro debe aparecer en el archivo de registros rechazados, con el motivo correspondiente.
- El registro no debe aparecer en el archivo de movimientos aceptados.
- La cantidad de registros leídos debe ser 1.
- La cantidad de movimientos aceptados debe ser 0.
- La cantidad de movimientos rechazados debe ser 1.
- No deben registrarse errores de validación en los demás campos.

## 6. Resultados obtenidos

Pendientes de ejecución.

## 7. Estado

Diseñado. No ejecutado.

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.