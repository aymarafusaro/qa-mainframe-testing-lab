# TC-BATCH-008 - Rechazo de registro con longitud inferior a la esperada

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros de entrada cuya longitud sea inferior a las 30 posiciones establecidas en el layout del archivo.

## 2. Precondiciones

- El programa `BNKTRN01` deberá validar que cada registro tenga exactamente 30 posiciones.
- El archivo de entrada deberá utilizar el layout definido para los movimientos bancarios.
- Los datos del registro deberán ser válidos en los campos que estén presentes.
- La cuenta ficticia `0001234567` deberá existir en el maestro de cuentas.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | Ausente |
| Longitud esperada | 30 posiciones |
| Longitud recibida | 29 posiciones |

### Registro de entrada

```text
00012345670000012505020261015
```

**Longitud del registro:** 29 caracteres.

El registro no contiene la posición 30, correspondiente al campo `TRANSACTION-TYPE`.

## 4. Pasos de ejecución

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Crear el archivo de entrada con el registro de 29 posiciones.
3. Verificar que el registro tenga exactamente 29 caracteres.
4. Ejecutar el programa `BNKTRN01`, una vez que esté implementado.
5. Inspeccionar los archivos de salida de registros aceptados y rechazados.
6. Verificar que el registro sea rechazado por longitud incorrecta.

## 5. Resultado esperado

- Cantidad de registros procesados: 1.
- Cantidad de registros aceptados: 0.
- Cantidad de registros rechazados: 1.
- Motivo del rechazo: longitud incorrecta del registro (29 posiciones en lugar de 30).
- El registro no deberá procesarse como un movimiento válido.
- No deberán generarse movimientos aceptados a partir de este registro.

## 6. Resultado obtenido

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes de ejecución.

No existen evidencias de ejecución real para este caso de prueba.