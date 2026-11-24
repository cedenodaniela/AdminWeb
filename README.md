# CanchApp · AdminWeb

Panel web de administración del **Complejo Deportivo Calceta** (Calceta, Manabí, Ecuador).

Angular standalone + Angular Material · TypeScript.

Este repositorio contiene **solo el panel web**. La API vive en `../Backend` y la app móvil en `../Frontend`.

## Documentación

La documentación general del proyecto **no vive aquí**: está en la carpeta de trabajo, un nivel arriba.

| Documento | Ruta |
|---|---|
| Guía para agentes y convenciones | `../AGENTS.md` |
| DERCAS (fuente de verdad) | `../DERCAS_CanchApp.pdf` |
| Addendum v0.3 (RF-18 a RF-23) | `../docs/DERCAS_CanchApp_v0.3_addendum.md` |
| Planificación de las 5 iteraciones | `../docs/PLANIFICACION.md` |

## Pantallas

| Pantalla | RF | Carpeta |
|---|---|---|
| Inicio de sesión | RF-18 | `src/app/auth/` |
| Tablero y agenda semanal | RF-19 | `src/app/tablero/` |
| Verificación de comprobantes | RF-20 | `src/app/comprobantes/` |
| Canchas, horarios, tarifas y bloqueos | RF-21 | `src/app/canchas/` |
| Configuración y usuarios administradores | RF-22 | `src/app/configuracion/` |
| Reportes y exportación a CSV | RF-23 | `src/app/reportes/` |

## Puesta en marcha

```bash
npm install
npm start
```

## Pruebas

```bash
npm test
npm run lint
npm run build
```

## Flujo de trabajo

Ramas `main` y `develop`; una rama por tarea y un Pull Request por RF. Los issues y milestones se gestionan en el repositorio `Backend`. Ver `../AGENTS.md` §12.

## Estado

En construcción. Corresponde a la iteración 5 del plan, después de que la API esté estable.
