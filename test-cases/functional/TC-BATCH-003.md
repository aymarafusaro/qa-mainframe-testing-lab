# TC-BATCH-003 - Rechazo por importe igual a cero

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento bancario cuyo importe sea igual a cero, aunque el formato del campo sea correcto y los demás datos cumplan con las reglas de validación.

## 2. Precondiciones

- El maestro de cuentas ficticio debe estar disponible.
- La cuenta `0001234567` debe existir en dicho maestro.
- El archivo de entrada debe contener un registro de 30 posiciones.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | 0001234567 |
| AMOUNT | 00000000000 |
| TRANSACTION-DATE | 20261015 |
| TRANSACTION-TYPE | C |

Registro completo de 30 posiciones:

`00012345670000000000020261015C`

### 3.1 Validaciones aplicables

- ACCOUNT-NUMBER: contiene exactamente 10 dígitos y existe en el maestro ficticio.
- AMOUNT: contiene exactamente 11 dígitos y es numérico.
- AMOUNT: su valor es igual a cero, por lo tanto incumple la regla de importe mayor que cero.
- TRANSACTION-DATE: tiene formato AAAAMMDD y representa una fecha calendario válida.
- TRANSACTION-TYPE: contiene el valor C.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el registro tenga exactamente 30 posiciones.
4. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado.
5. Revisar la salida de movimientos aceptados.
6. Revisar la salida de registros rechazados.
7. Verificar el motivo informado para el rechazo.

## 5. Resultados esperados

- El registro debe ser rechazado.
- El motivo de rechazo debe identificar que el importe es igual a cero o que no cumple la regla de importe mayor que cero.
- La cantidad de movimientos aceptados debe ser 0.
- La cantidad de movimientos rechazados debe ser 1.
- No deben registrarse errores en los demás campos.

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.