# TC-BATCH-008 - Rechazo de registro con cuenta bancaria en blanco

## 1. Objetivo

Verificar que el programa `BNKTRN01` rechace los registros cuya cuenta bancaria se encuentre en blanco, dado que es un campo obligatorio del layout de entrada.

## 2. Precondiciones

- El archivo de entrada deberá ser secuencial QSAM de longitud fija (`RECFM=FB`).
- La longitud de cada registro deberá ser de exactamente 30 posiciones (`LRECL=30`).
- El programa `BNKTRN01` deberá validar que la cuenta bancaria sea un campo obligatorio y contenga únicamente dígitos.
- El resto de los campos del registro deberá contener valores válidos.
- La cuenta bancaria no deberá consultarse en el maestro de cuentas cuando el campo se encuentre en blanco.

## 3. Datos de prueba

**Registro de entrada:**

```text
          0000012505020261015C
```

**Desglose del registro:**

| Campo | Posiciones | Valor |
|---|---|---|
| ACCOUNT-NUMBER | 1-10 | 10 espacios en blanco |
| AMOUNT | 11-21 | `00000125050` |
| TRANSACTION-DATE | 22-29 | `20261015` |
| TRANSACTION-TYPE | 30 | `C` |

**Interpretación de los datos:**

- Cuenta bancaria: en blanco.
- Importe: 1.250,50.
- Fecha de operación: 15/10/2026.
- Tipo de movimiento: crédito.

## 4. Pasos de ejecución

1. Preparar un archivo de entrada con el registro definido en los datos de prueba.
2. Verificar que el registro tenga exactamente 30 posiciones.
3. Ejecutar el programa `BNKTRN01` mediante el JCL correspondiente.
4. Verificar el procesamiento del registro.
5. Consultar el archivo de salida de registros aceptados.
6. Consultar el archivo de salida de registros rechazados y el motivo informado.

## 5. Resultados esperados

- El programa deberá leer un registro.
- El registro deberá ser rechazado porque la cuenta bancaria se encuentra en blanco.
- El programa deberá identificar la cuenta bancaria como un campo obligatorio.
- El registro no deberá incluirse en el archivo de movimientos aceptados.
- El registro deberá incluirse en el archivo de movimientos rechazados.
- El motivo del rechazo deberá indicar que la cuenta bancaria está en blanco.
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