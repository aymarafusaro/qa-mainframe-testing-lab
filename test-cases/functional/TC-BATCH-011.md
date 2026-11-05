# TC-BATCH-011 - Rechazo de registro con fecha no numérica

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros cuya fecha de transacción contenga caracteres no numéricos, incumpliendo el formato establecido `AAAAMMDD`.

## 2. Precondiciones

- El programa `BNKTRN01` deberá validar que la fecha de transacción tenga exactamente 8 caracteres numéricos.
- El archivo de entrada deberá utilizar el layout definido para los movimientos bancarios.
- La cuenta ficticia `0001234567` deberá existir en el maestro de cuentas.
- Los campos de cuenta, importe y tipo de movimiento deberán contener valores válidos.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `2026A015` |
| TRANSACTION-TYPE | `C` |
| Longitud esperada | 30 posiciones |
| Longitud recibida | 30 posiciones |

### Registro de entrada

```text
0001234567000001250502026A015C
```

**Longitud del registro:** 30 caracteres.

El campo `TRANSACTION-DATE` contiene una letra (`A`) en lugar de un dígito numérico, por lo que incumple el formato `AAAAMMDD`.

## 4. Pasos de ejecución

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Crear el archivo de entrada con el registro definido para esta prueba.
3. Verificar que el registro tenga exactamente 30 caracteres.
4. Ejecutar el programa `BNKTRN01`, una vez que esté implementado.
5. Inspeccionar los archivos de salida de registros aceptados y rechazados.
6. Verificar que el registro sea rechazado por contener caracteres no numéricos en la fecha.

## 5. Resultado esperado

- Cantidad de registros procesados: 1.
- Cantidad de registros aceptados: 0.
- Cantidad de registros rechazados: 1.
- Motivo del rechazo: formato de fecha inválido por contener caracteres no numéricos (`2026A015`).
- El registro no deberá procesarse como un movimiento válido.
- No deberán generarse movimientos aceptados a partir de este registro.

## 6. Resultado obtenido

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes de ejecución.

No existen evidencias de ejecución real para este caso de prueba.