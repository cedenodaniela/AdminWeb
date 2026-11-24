# AGENTS.md — CanchApp · AdminWeb

Panel web de administración en **Angular standalone + Angular Material** del proyecto **CanchApp**. Esta es la guía **breve** de este repositorio.

> **La guía completa vive fuera de este repositorio**, en la carpeta de trabajo, un nivel arriba:
> [`../AGENTS.md`](../AGENTS.md) · DERCAS: [`../DERCAS_CanchApp.pdf`](../DERCAS_CanchApp.pdf) · addendum v0.3 (RF-18 a RF-23): [`../docs/DERCAS_CanchApp_v0.3_addendum.md`](../docs/DERCAS_CanchApp_v0.3_addendum.md) · plan: [`../docs/PLANIFICACION.md`](../docs/PLANIFICACION.md).
>
> Si este archivo y la guía completa se contradicen, manda la guía completa y, sobre todo, el **DERCAS y el addendum**.

## Qué se construye aquí

La gestión del complejo **desde computadora o tablet**. Cubre **RF-18 a RF-23**.

- `src/app/auth/` — inicio de sesión del panel (RF-18).
- `src/app/tablero/` — tablero y agenda semanal (RF-19).
- `src/app/comprobantes/` — bandeja de verificación (RF-20).
- `src/app/canchas/` — canchas, horarios, tarifas y bloqueos (RF-21).
- `src/app/configuracion/` — datos del complejo, políticas y usuarios administradores (RF-22).
- `src/app/reportes/` — indicadores y exportación (RF-23).
- `src/app/core/` — autenticación, interceptor JWT, guard de `ADMINISTRADOR`, servicios HTTP y WebSocket.
- `src/app/shared/` — tabla, paginador, pipes de fecha y estado.

La app móvil es otro repositorio (`../Frontend`). **El panel no reemplaza a la app**: el administrador opera desde el celular en el complejo y gestiona desde el navegador en escritorio.

## Reglas que no se rompen

- **La UI no calcula reglas de negocio.** Totales, plazos, límites y estados llegan resueltos desde la API.
- **Angular Material** para tablas, filtros, formularios y calendario, adaptado a la paleta institucional.
- El JWT va por interceptor HTTP y el guard exige `ADMINISTRADOR`. **Ninguna pantalla se renderiza antes de validar la sesión.**
- Tablas con encabezado fijo, orden por columna, paginación y filtros visibles. **Nunca** cargues una lista completa sin paginar.
- Responsive desde **1280 × 720**; las tablas anchas hacen scroll dentro de su propio contenedor.
- **Fechas y horas** con `Intl.DateTimeFormat` y `timeZone: 'America/Guayaquil'`.
- **Paleta**: verde `#0F6B3E`, azul `#1D5FA8`, naranja `#B4541A`, rojo `#B42318`, fondo `#F4F6F1`.
- **Terminología: «tablero»**, nunca «dashboard». El tablero muestra el **«cobrado del día»** (transferencias aprobadas + efectivo registrado, sin saldo aplicado); los ingresos completos son de los reportes (RF-17).
- **Confirmación explícita** antes de acciones destructivas: desactivar una cancha con reservas, rechazar un comprobante, eliminar un bloqueo, desactivar un administrador.
- **La exportación CSV la genera el backend**, no el navegador.
- **El panel no recibe notificaciones push.** Los avisos se muestran dentro de la interfaz.
- Cambios en tiempo real por **WebSocket (STOMP)** mientras el panel está abierto; al reconectar, se recarga la vista.
- **El pago en efectivo (P4) no se hace aquí**: es solo de la app móvil.

## Comandos

```bash
npm install
npm start
npm test
npm run lint
npm run build
```

## Pruebas y cierre

- Cada pantalla tiene su prueba de componente; cada RF del panel, su prueba de endpoint en `Backend`.
- Un RF del panel **no está terminado si solo se probó la pantalla**.
- Antes de commitear: `npm test` y `npm run lint` en verde.
- Un commit por cambio lógico, Conventional Commits en español, citando el RF.

## Contrato con el backend

Consume la API `/api/v1` de `../Backend`. El `openapi.json` de ese repositorio es el **contrato**: si un DTO cambia, se detecta en el Pull Request.

## Seguridad

**Nunca** subas secretos ni credenciales. Las cuentas de administrador se crean desde el panel (RF-22) con enlace de invitación de un solo uso.
