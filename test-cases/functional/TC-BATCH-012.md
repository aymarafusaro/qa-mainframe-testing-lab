# TC-BATCH-012 - Rechazo de registro con tipo de movimiento inválido

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros cuyo tipo de movimiento no corresponda a los valores permitidos en el layout del archivo.

## 2. Precondiciones

- El programa `BNKTRN01` deberá validar que el tipo de movimiento sea `C` (crédito) o `D` (débito).
- El archivo de entrada deberá utilizar el layout definido para los movimientos bancarios.
- La cuenta ficticia `0001234567` deberá existir en el maestro de cuentas.
- Los campos de cuenta, importe y fecha deberán contener valores válidos.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | `X` |
| Valores permitidos | `C` o `D` |
| Longitud esperada | 30 posiciones |
| Longitud recibida | 30 posiciones |

### Registro de entrada

```text
00012345670000012505020261015X
```

**Longitud del registro:** 30 caracteres.

El campo `TRANSACTION-TYPE` contiene el valor `X`, que no está contemplado entre los tipos de movimiento permitidos (`C` y `D`).

## 4. Pasos de ejecución

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Crear el archivo de entrada con el registro definido para esta prueba.
3. Verificar que el registro tenga exactamente 30 caracteres.
4. Ejecutar el programa `BNKTRN01`, una vez que esté implementado.
5. Inspeccionar los archivos de salida de registros aceptados y rechazados.
6. Verificar que el registro sea rechazado por tipo de movimiento inválido.

## 5. Resultado esperado

- Cantidad de registros procesados: 1.
- Cantidad de registros aceptados: 0.
- Cantidad de registros rechazados: 1.
- Motivo del rechazo: tipo de movimiento inválido (`X`).
- El registro no deberá procesarse como un movimiento válido.
- No deberán generarse movimientos aceptados a partir de este registro.

## 6. Resultado obtenido

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes de ejecución.

No existen evidencias de ejecución real para este caso de prueba.