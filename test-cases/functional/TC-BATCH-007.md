# TC-BATCH-007 - Aceptación de importe máximo válido

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` acepte un movimiento bancario cuyo importe sea igual al máximo permitido de 999.999.999,99, siempre que los demás campos cumplan con las reglas de validación.

## 2. Precondiciones

- El maestro de cuentas ficticio debe estar disponible.
- La cuenta `0001234567` debe existir en dicho maestro.
- El archivo de entrada debe contener un registro de 30 posiciones.
- El importe máximo permitido debe ser 999.999.999,99.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | 0001234567 |
| AMOUNT | 99999999999 |
| TRANSACTION-DATE | 20261015 |
| TRANSACTION-TYPE | C |

Registro completo de 30 posiciones:

`00012345679999999999920261015C`

### 3.1 Validaciones aplicables

- ACCOUNT-NUMBER: contiene exactamente 10 dígitos y existe en el maestro ficticio.
- AMOUNT: contiene exactamente 11 dígitos y es numérico.
- AMOUNT: representa un valor de 999.999.999,99, equivalente al máximo permitido.
- TRANSACTION-DATE: tiene formato AAAAMMDD y representa una fecha calendario válida.
- TRANSACTION-TYPE: contiene el valor C.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el registro tenga exactamente 30 posiciones.
4. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado.
5. Revisar la salida de movimientos aceptados.
6. Revisar la salida de registros rechazados.
7. Verificar que el movimiento haya sido aceptado con el importe máximo permitido.

## 5. Resultados esperados

- El registro debe ser aceptado.
- La cantidad de movimientos aceptados debe ser 1.
- La cantidad de movimientos rechazados debe ser 0.
- El importe procesado debe corresponder a 999.999.999,99.
- No deben registrarse errores de validación.

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.