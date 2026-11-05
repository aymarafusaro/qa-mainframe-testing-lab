# TC-BATCH-010 - Rechazo de registro con fecha inexistente

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros cuya fecha de transacción tenga un formato válido, pero represente una fecha inexistente en el calendario.

## 2. Precondiciones

- El programa `BNKTRN01` deberá validar que la fecha de transacción tenga el formato `AAAAMMDD`.
- El programa deberá comprobar que la fecha corresponda a un día válido del calendario.
- El archivo de entrada deberá utilizar el layout definido para los movimientos bancarios.
- La cuenta ficticia `0001234567` deberá existir en el maestro de cuentas.
- Los campos de cuenta, importe y tipo de movimiento deberán contener valores válidos.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20260230` |
| TRANSACTION-TYPE | `C` |
| Longitud esperada | 30 posiciones |
| Longitud recibida | 30 posiciones |

### Registro de entrada

```text
00012345670000012505020260230C
```

**Longitud del registro:** 30 caracteres.

La fecha `20260230` respeta el formato `AAAAMMDD`, pero representa un día inexistente, ya que febrero de 2026 tiene 28 días.

## 4. Pasos de ejecución

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Crear el archivo de entrada con el registro definido para esta prueba.
3. Verificar que el registro tenga exactamente 30 caracteres.
4. Ejecutar el programa `BNKTRN01`, una vez que esté implementado.
5. Inspeccionar los archivos de salida de registros aceptados y rechazados.
6. Verificar que el registro sea rechazado por fecha inexistente.

## 5. Resultado esperado

- Cantidad de registros procesados: 1.
- Cantidad de registros aceptados: 0.
- Cantidad de registros rechazados: 1.
- Motivo del rechazo: fecha de transacción inexistente en el calendario (`20260230`).
- El registro no deberá procesarse como un movimiento válido.
- No deberán generarse movimientos aceptados a partir de este registro.

## 6. Resultado obtenido

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes de ejecución.

No existen evidencias de ejecución real para este caso de prueba.