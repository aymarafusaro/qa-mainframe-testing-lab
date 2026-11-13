# TC-BATCH-009 - Rechazo de registro con tipo de movimiento en blanco

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros cuyo tipo de movimiento se encuentre en blanco, dado que es un campo obligatorio del layout de entrada y solamente admite los valores `C` (crédito) o `D` (débito).

## 2. Precondiciones

- El archivo de entrada deberá ser secuencial QSAM de longitud fija (`RECFM=FB`).
- La longitud de cada registro deberá ser de exactamente 30 posiciones (`LRECL=30`).
- El programa `BNKTRN01` deberá validar que el tipo de movimiento sea un campo obligatorio.
- El campo `TRANSACTION-TYPE` solamente deberá admitir los valores `C` o `D`.
- El resto de los campos del registro deberá contener valores válidos.
- La cuenta bancaria utilizada deberá existir en el maestro ficticio de cuentas.

## 3. Datos de prueba

**Registro de entrada:**

```text
00012345670000012505020261015 
```

**Desglose del registro:**

| Campo | Posiciones | Valor |
|---|---|---|
| ACCOUNT-NUMBER | 1-10 | `0001234567` |
| AMOUNT | 11-21 | `00000125050` |
| TRANSACTION-DATE | 22-29 | `20261015` |
| TRANSACTION-TYPE | 30 | 1 espacio en blanco |

**Interpretación de los datos:**

- Cuenta bancaria: `0001234567`.
- Importe: 1.250,50.
- Fecha de operación: 15/10/2026.
- Tipo de movimiento: en blanco.

## 4. Pasos de ejecución

1. Preparar un archivo de entrada con el registro definido en los datos de prueba.
2. Verificar que el registro tenga exactamente 30 posiciones.
3. Ejecutar el programa `BNKTRN01` mediante el JCL correspondiente.
4. Verificar el procesamiento del registro.
5. Consultar el archivo de salida de registros aceptados.
6. Consultar el archivo de salida de registros rechazados y el motivo informado.

## 5. Resultados esperados

- El programa deberá leer un registro.
- El registro deberá ser rechazado porque el tipo de movimiento se encuentra en blanco.
- El programa deberá identificar `TRANSACTION-TYPE` como un campo obligatorio.
- El programa no deberá aceptar el registro como crédito ni como débito.
- El registro no deberá incluirse en el archivo de movimientos aceptados.
- El registro deberá incluirse en el archivo de movimientos rechazados.
- El motivo del rechazo deberá indicar que el tipo de movimiento está en blanco.
- El procesamiento deberá finalizar correctamente, sin interrupciones inesperadas.

**Resumen esperado:**

| Resultado | Cantidad |
|---|---:|
| Registros leídos | 1 |
| Registros aceptados | 0 |
| Registros rechazados | 1 |

## 6. Resultados obtenidos

Pendiente de ejecución.

## 7. Estado

**Diseñado. No ejecutado.**

## 8. Evidencias

Pendientes de ejecución.

No se dispone todavía de evidencias de ejecución real.