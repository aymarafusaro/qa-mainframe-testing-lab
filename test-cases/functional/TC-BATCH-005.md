# TC-BATCH-005 - Rechazo por importe con caracteres no numéricos

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento cuyo importe contiene caracteres no numéricos, aunque la longitud del campo sea correcta y los demás datos cumplan con las reglas de validación.

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
- `AMOUNT`: debe contener exactamente 11 caracteres numéricos.
- `AMOUNT`: no debe contener letras, espacios ni otros caracteres no numéricos.
- Validación de formato: el contenido de `AMOUNT` debe validarse antes de realizar cualquier conversión o cálculo numérico.
- `TRANSACTION-DATE`: debe tener formato AAAAMMDD y representar una fecha calendario válida.
- `TRANSACTION-TYPE`: debe contener `C` (crédito) o `D` (débito).

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `0000012A050` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | `C` |

**Registro completo de 30 posiciones:**

`00012345670000012A05020261015C`

**Precondiciones:**

- El maestro de cuentas ficticio debe estar disponible para el procesamiento.
- La cuenta `0001234567` debe existir en el maestro.
- Los campos de fecha y tipo de movimiento deben contener valores válidos.
- El campo `AMOUNT` debe contener 11 caracteres, incluyendo la letra `A` en lugar de un dígito.
- El único dato que incumple las reglas de validación es el contenido no numérico del importe.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el archivo esté definido como secuencial QSAM, con `RECFM=FB` y `LRECL=30`.
4. Verificar que el registro de entrada contenga exactamente 30 posiciones.
5. Verificar que `AMOUNT` contenga exactamente 11 caracteres y que incluya la letra `A`.
6. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado y disponible para pruebas.
7. Revisar la salida de movimientos aceptados.
8. Revisar la salida de registros rechazados y los contadores del procesamiento.
9. Verificar que el motivo de rechazo corresponda al formato no numérico de `AMOUNT`.

## 5. Resultados esperados

- El registro debe ser leído correctamente por el programa.
- La cuenta debe superar las validaciones de formato y existencia.
- El programa debe identificar que `AMOUNT` contiene un carácter no numérico.
- El registro debe ser rechazado por formato inválido del importe.
- La validación de formato debe impedir que el valor se utilice en conversiones o cálculos numéricos.
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