# TC-BATCH-010 - Rechazo de registro con fecha inexistente

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento bancario cuya fecha de transacción tenga un formato válido, pero represente una fecha inexistente en el calendario.

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
- `AMOUNT`: debe contener exactamente 11 dígitos, ser numérico y ser mayor que cero.
- `TRANSACTION-DATE`: debe contener exactamente 8 dígitos numéricos en formato AAAAMMDD.
- `TRANSACTION-DATE`: además de cumplir con el formato, debe representar una fecha calendario existente.
- `TRANSACTION-TYPE`: debe contener `C` (crédito) o `D` (débito).

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20260230` |
| TRANSACTION-TYPE | `C` |

**Registro completo de 30 posiciones:**

`00012345670000012505020260230C`

**Interpretación de la fecha:** `20260230` respeta el formato `AAAAMMDD`, pero representa una fecha inexistente, ya que febrero de 2026 tiene 28 días.

**Interpretación del importe:** `00000125050` representa 1.250,50, ya que los dos decimales son implícitos.

**Precondiciones:**

- El maestro de cuentas ficticio debe estar disponible para el procesamiento.
- La cuenta `0001234567` debe existir en el maestro de cuentas.
- Los campos de cuenta, importe y tipo de movimiento deben cumplir con sus respectivas reglas de validación.
- La fecha de transacción debe ser rechazada exclusivamente por no representar un día válido del calendario.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el archivo esté definido como secuencial QSAM, con `RECFM=FB` y `LRECL=30`.
4. Verificar que el registro de entrada contenga exactamente 30 posiciones.
5. Verificar que el campo `TRANSACTION-DATE` contenga ocho dígitos numéricos y represente la fecha inexistente `20260230`.
6. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado y disponible para pruebas.
7. Revisar la salida de movimientos aceptados.
8. Revisar la salida de registros rechazados y los contadores del procesamiento.
9. Verificar que el motivo de rechazo identifique que la fecha no existe en el calendario.

## 5. Resultados esperados

- El registro debe ser leído correctamente por el programa.
- La cuenta debe superar las validaciones de formato y existencia.
- El importe debe superar la validación de formato numérico y de valor mayor que cero.
- El tipo de movimiento debe superar su validación.
- La fecha debe superar la validación de formato numérico y estructural.
- El programa debe identificar que `20260230` no representa una fecha calendario válida.
- El registro debe ser rechazado por fecha inexistente.
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