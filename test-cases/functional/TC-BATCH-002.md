# TC-BATCH-002 - Rechazo por cuenta inexistente

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento bancario cuya cuenta tenga un formato válido, pero no exista en el maestro de cuentas ficticio.

## 2. Precondiciones

- El maestro de cuentas ficticio debe estar disponible.
- La cuenta `9999999999` no debe existir en dicho maestro.
- El archivo de entrada debe contener un registro de 30 posiciones.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | 9999999999 |
| AMOUNT | 00000125050 |
| TRANSACTION-DATE | 20261015 |
| TRANSACTION-TYPE | C |

Registro completo de 30 posiciones:

`99999999990000012505020261015C`

### 3.1 Validaciones aplicables

- ACCOUNT-NUMBER: contiene exactamente 10 dígitos.
- AMOUNT: es numérico y mayor que cero.
- TRANSACTION-DATE: tiene formato AAAAMMDD y representa una fecha calendario válida.
- TRANSACTION-TYPE: contiene el valor C.
- Existencia de cuenta: la cuenta no se encuentra en el maestro ficticio.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio sin la cuenta `9999999999`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el registro tenga exactamente 30 posiciones.
4. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado.
5. Revisar la salida de movimientos aceptados.
6. Revisar la salida de registros rechazados.
7. Verificar el motivo informado para el rechazo.

## 5. Resultados esperados

- El registro debe ser rechazado.
- El motivo de rechazo debe identificar que la cuenta no existe.
- La cantidad de movimientos aceptados debe ser 0.
- La cantidad de movimientos rechazados debe ser 1.
- No debe producirse una aceptación del movimiento.

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.