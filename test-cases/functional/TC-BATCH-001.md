# TC-BATCH-001 - Validación de movimiento bancario válido

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` procese correctamente un movimiento bancario que cumple con todas las reglas de validación definidas.

## 2. Diseño del registro de entrada

El programa recibirá un archivo secuencial de longitud fija. Cada registro tendrá 30 posiciones.

| Campo | Posición inicial | Posición final | Longitud | Formato COBOL | Descripción |
|---|---|---|---|---|---|
| ACCOUNT-NUMBER | 1 | 10 | 10 | PIC X(10) | Número de cuenta |
| AMOUNT | 11 | 21 | 11 | PIC 9(9)V99 | Importe con dos decimales implícitos |
| TRANSACTION-DATE | 22 | 29 | 8 | PIC X(8) | Fecha en formato AAAAMMDD |
| TRANSACTION-TYPE | 30 | 30 | 1 | PIC X | Tipo de movimiento |

### 2.1 Reglas de validación

- **ACCOUNT-NUMBER:** obligatorio, debe contener únicamente dígitos y existir en el maestro de cuentas ficticio.
- **AMOUNT:** debe ser numérico y mayor que cero. El rango permitido es de 0,01 a 999.999.999,99.
- **TRANSACTION-DATE:** debe representar una fecha calendario válida en formato AAAAMMDD.
- **TRANSACTION-TYPE:** debe contener `C` (crédito) o `D` (débito).

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | 0001234567 |
| AMOUNT | 00000125050 |
| TRANSACTION-DATE | 20261015 |
| TRANSACTION-TYPE | C |

Registro completo de 30 posiciones:

`00012345670000012505020261015C`

Precondición: la cuenta ficticia `0001234567` debe existir en el maestro de cuentas de prueba.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el registro tenga exactamente 30 posiciones.
4. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado.
5. Revisar la salida de movimientos aceptados.
6. Revisar la salida de registros rechazados.

## 5. Resultados esperados

- El registro debe ser aceptado.
- La cantidad de movimientos aceptados debe ser 1.
- La cantidad de movimientos rechazados debe ser 0.
- No deben registrarse errores de validación.

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.

