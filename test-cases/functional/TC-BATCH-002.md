# TC-BATCH-002 - Rechazo por cuenta inexistente

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento bancario cuya cuenta tenga un formato válido, pero no exista en el maestro de cuentas ficticio.

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

- `ACCOUNT-NUMBER`: contiene exactamente 10 caracteres numéricos.
- Existencia de cuenta: la cuenta debe encontrarse en el maestro de cuentas ficticio.
- `AMOUNT`: es numérico y mayor que cero.
- `TRANSACTION-DATE`: tiene formato AAAAMMDD y representa una fecha calendario válida.
- `TRANSACTION-TYPE`: contiene `C` (crédito) o `D` (débito).

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `9999999999` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | `C` |

**Registro completo de 30 posiciones:**

`99999999990000012505020261015C`

**Interpretación del importe:** `00000125050` representa 1.250,50, ya que los dos decimales son implícitos.

**Precondiciones:**

- El maestro de cuentas ficticio debe estar disponible para el procesamiento.
- La cuenta `9999999999` no debe existir en el maestro de cuentas.
- Los demás campos del registro deben cumplir con sus respectivas reglas de validación.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio sin la cuenta `9999999999`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el archivo esté definido como secuencial QSAM, con `RECFM=FB` y `LRECL=30`.
4. Verificar que el registro de entrada contenga exactamente 30 posiciones.
5. Verificar que el número de cuenta tenga 10 dígitos y que no exista en el maestro ficticio.
6. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado y disponible para pruebas.
7. Revisar la salida de movimientos aceptados.
8. Revisar la salida de registros rechazados y los contadores del procesamiento.
9. Verificar que el motivo de rechazo identifique la inexistencia de la cuenta.

## 5. Resultados esperados

- El registro debe ser leído correctamente por el programa.
- El número de cuenta debe superar la validación de formato.
- El programa debe identificar que la cuenta `9999999999` no existe en el maestro ficticio.
- El registro debe ser rechazado por cuenta inexistente.
- El registro debe aparecer en el archivo de registros rechazados, con el motivo correspondiente.
- El registro no debe aparecer en el archivo de movimientos aceptados.
- La cantidad de registros leídos debe ser 1.
- La cantidad de movimientos aceptados debe ser 0.
- La cantidad de movimientos rechazados debe ser 1.

## 6. Resultados obtenidos

Pendientes de ejecución.

## 7. Estado

Diseñado. No ejecutado.

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.