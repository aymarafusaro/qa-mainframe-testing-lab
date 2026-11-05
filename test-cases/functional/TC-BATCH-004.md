# TC-BATCH-004 - Rechazo por cuenta con caracteres no numéricos

## 1. Objetivo

Verificar que el programa COBOL Batch `BNKTRN01` rechace un movimiento cuya cuenta bancaria contiene caracteres no numéricos, aunque la longitud del campo sea correcta y los demás datos cumplan con las reglas de validación.

## 2. Precondiciones

- El archivo de entrada debe contener un registro de 30 posiciones.
- El programa debe validar que `ACCOUNT-NUMBER` contenga exclusivamente dígitos.
- Los demás campos del registro deben cumplir con sus reglas de validación.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | 00012A4567 |
| AMOUNT | 00000125050 |
| TRANSACTION-DATE | 20261015 |
| TRANSACTION-TYPE | C |

Registro completo de 30 posiciones:

`00012A45670000012505020261015C`

### 3.1 Validaciones aplicables

- ACCOUNT-NUMBER: contiene exactamente 10 caracteres.
- ACCOUNT-NUMBER: contiene la letra A, por lo tanto no cumple con la regla de contenido exclusivamente numérico.
- AMOUNT: contiene exactamente 11 dígitos y es numérico.
- AMOUNT: representa un valor de 1.250,50, mayor que cero.
- TRANSACTION-DATE: tiene formato AAAAMMDD y representa una fecha calendario válida.
- TRANSACTION-TYPE: contiene el valor C.

## 4. Pasos de prueba

1. Preparar el archivo de entrada con el registro definido en este caso.
2. Verificar que el registro tenga exactamente 30 posiciones.
3. Ejecutar el programa `BNKTRN01` cuando se encuentre implementado.
4. Revisar la salida de movimientos aceptados.
5. Revisar la salida de registros rechazados.
6. Verificar que el motivo informado corresponda al formato inválido de ACCOUNT-NUMBER.

## 5. Resultados esperados

- El registro debe ser rechazado.
- El motivo de rechazo debe indicar que ACCOUNT-NUMBER contiene caracteres no numéricos o tiene un formato inválido.
- La cantidad de movimientos aceptados debe ser 0.
- La cantidad de movimientos rechazados debe ser 1.
- No deben registrarse errores en los demás campos.

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes. No existen evidencias de ejecución real en esta etapa.