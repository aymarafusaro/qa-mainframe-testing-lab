# TC-BATCH-009 - Rechazo de registro con longitud superior a la esperada

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros de entrada cuya longitud sea superior a las 30 posiciones establecidas en el layout del archivo.

## 2. Precondiciones

- El programa `BNKTRN01` deberá validar que cada registro tenga exactamente 30 posiciones.
- El archivo de entrada deberá utilizar el layout definido para los movimientos bancarios.
- Los datos correspondientes a los primeros 30 caracteres deberán ser válidos.
- La cuenta ficticia `0001234567` deberá existir en el maestro de cuentas.

## 3. Datos de prueba

| Campo | Valor |
|---|---|
| ACCOUNT-NUMBER | `0001234567` |
| AMOUNT | `00000125050` |
| TRANSACTION-DATE | `20261015` |
| TRANSACTION-TYPE | `C` |
| Carácter adicional | `X` |
| Longitud esperada | 30 posiciones |
| Longitud recibida | 31 posiciones |

### Registro de entrada

```text
00012345670000012505020261015CX
```

**Longitud del registro:** 31 caracteres.

La posición 31 contiene un carácter adicional (`X`), que no forma parte del layout definido.

## 4. Pasos de ejecución

1. Preparar el maestro de cuentas ficticio con la cuenta `0001234567`.
2. Crear el archivo de entrada con el registro de 31 posiciones.
3. Verificar que el registro tenga exactamente 31 caracteres.
4. Ejecutar el programa `BNKTRN01`, una vez que esté implementado.
5. Inspeccionar los archivos de salida de registros aceptados y rechazados.
6. Verificar que el registro sea rechazado por longitud incorrecta.

## 5. Resultado esperado

- Cantidad de registros procesados: 1.
- Cantidad de registros aceptados: 0.
- Cantidad de registros rechazados: 1.
- Motivo del rechazo: longitud incorrecta del registro (31 posiciones en lugar de 30).
- El registro no deberá procesarse como un movimiento válido.
- No deberán generarse movimientos aceptados a partir de este registro.

## 6. Resultado obtenido

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes de ejecución.

No existen evidencias de ejecución real para este caso de prueba.