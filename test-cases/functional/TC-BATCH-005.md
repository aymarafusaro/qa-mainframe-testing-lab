# TC-BATCH-005 - Rechazo por importe con caracteres no numéricos

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento cuyo importe contiene caracteres no numéricos, aunque la longitud del campo sea correcta y los demás datos cumplan con las reglas de validación.

## 2. Precondiciones

- El archivo de entrada debe contener un registro de 30 posiciones.
- La cuenta `0001234567` debe existir en el maestro ficticio.
- El programa debe validar que `AMOUNT` contenga exclusivamente dígitos.
- Los demás campos del registro deben cumplir con sus reglas de validación.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | 0001234567 |
| AMOUNT | 0000012A050 |
| TRANSACTION-DATE | 20261015 |
| TRANSACTION-TYPE | C |

Registro completo de 30 posiciones:

`00012345670000012A05020261015C`

### 3.1 Validaciones aplicables

- ACCOUNT-NUMBER: contiene exactamente 10 dígitos y existe en el maestro ficticio.
- AMOUNT: contiene exactamente 11 caracteres.
- AMOUNT: contiene la letra A, por lo tanto no cumple con la regla de contenido exclusivamente numérico.
- TRANSACTION-DATE: tiene formato AAAAMMDD y representa una fecha calendario válida.
- TRANSACTION-TYPE: contiene el valor C.

## 4. Pasos de prueba

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Preparar el archivo de entrada con el registro definido en este caso.
3. Verificar que el registro tenga exactamente 30 posiciones.
4. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado.
5. Revisar la salida de movimientos aceptados.
6. Revisar la salida de registros rechazados.
7. Verificar que el motivo informado corresponda al importe con caracteres no numéricos.

## 5. Resultados esperados

- El registro debe ser rechazado.
- El motivo de rechazo debe indicar que AMOUNT contiene caracteres no numéricos o tiene un formato inválido.
- La cantidad de movimientos aceptados debe ser 0.
- La cantidad de movimientos rechazados debe ser 1.
- No deben registrarse errores en los demás campos.

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.