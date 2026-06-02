# 📦 Sistema de Gestión de Pedidos

Aplicación web para el control y seguimiento de pedidos de negocio, desarrollada bajo metodología Scrum en dos sprints. Permite registrar pedidos, gestionar clientes, cambiar estados y exportar reportes diarios.

---

## 👤 Equipo

| Nombre | Rol |
|---|---|
| Helmer Jose Torres Correa | Product Owner / Scrum Master / Developer |

---

## 🚀 Funcionalidades

### Sprint 1
- **US-01 – Registro de pedido:** Ingreso de cliente, productos, cantidades y cálculo automático del total. El pedido se guarda con fecha y estado "Pendiente".
- **US-02 – Lista de pedidos activos:** Visualización de todos los pedidos del día con su estado, ordenables por hora o estado.
- **US-03 – Cambio de estado:** Transición entre los estados `Pendiente → En proceso → Entregado`. No se permite revertir un pedido ya entregado.

### Sprint 2
- **US-04 – Historial de cliente:** Búsqueda por nombre con historial de pedidos anteriores, fechas y montos.
- **US-05 – Resumen del día:** Dashboard con cantidad de pedidos entregados y total vendido, actualizado automáticamente.
- **US-06 – Eliminar pedido:** Eliminación de pedidos pendientes con confirmación. Los pedidos entregados no se pueden eliminar.
- **US-07 – Exportar pedidos:** Generación de archivo CSV con cliente, productos, total y estado del día seleccionado.

---

## 🗂️ Estructura del proyecto

```
/lib
  ├── types.ts          → Tipos TypeScript (Order, Client, Product, etc.)
  ├── mock-data.ts      → Datos de ejemplo con clientes y pedidos
  └── export-csv.ts     → Utilidad de exportación CSV

/components
  ├── layout/           → app-sidebar, header, breadcrumbs
  ├── dashboard/        → stats-card, stats-grid
  ├── pedidos/          → orders-table, order-filters, order-status-badge
  └── shared/           → export-csv-button, search-input

/app/(dashboard)
  ├── layout.tsx        → Layout con sidebar compartido
  ├── page.tsx          → Dashboard principal
  ├── pedidos/          → Lista, nuevo y detalle de pedido
  ├── clientes/         → Lista y detalle de cliente
  ├── reportes/         → Visualización de datos de ventas
  └── ajustes/          → Configuración básica
```

---

## 🛠️ Herramientas de IA utilizadas

| Herramienta | Uso en el proyecto |
|---|---|
| **ChatGPT** | Definición de criterios de aceptación del backlog y refinamiento de historias de usuario |
| **Claude** | Resumen de sprint, actas de reunión y auditoría con Claude Code |
| **V0** | Diseño de UI (wireframes), código de pedidos y módulo de reportes |
| **Google Stitch** | Wireframing inicial de la interfaz |
| **OpenCode** | Código base del sprint 2 (módulo de clientes) |
| **GitHub Copilot (VS Code)** | Optimización y limpieza del código en el sprint 2 |

---

## 📋 Backlog

| ID | Tipo | Sprint | Puntos | Prioridad |
|---|---|---|---|---|
| US-01 | Registro de pedido | Sprint 1 | 5 | Alta |
| US-02 | Lista de pedidos activos | Sprint 1 | 3 | Alta |
| US-03 | Cambio de estado | Sprint 1 | 3 | Alta |
| US-04 | Historial de cliente | Sprint 2 | 5 | Media |
| US-05 | Resumen del día | Sprint 2 | 3 | Media |
| US-06 | Eliminar pedido | Sprint 2 | 2 | Baja |
| US-07 | Exportar pedidos | Sprint 2 | 3 | Baja |

**Total de puntos:** 24

---

## ✅ Estado del proyecto

- **Sprint 1:** ✅ Completado — Registro, listado y cambio de estado de pedidos implementados.
- **Sprint 2:** ✅ Completado — Historial de clientes (con tier: Regular / VIP / Premium), resumen diario, eliminación y exportación CSV implementados.

---

## 📝 Notas

- El IVA aplicado en la creación de pedidos es del **16%**.
- El dashboard se actualiza automáticamente al cambiar de día.
- El perfil de cliente incluye un sistema de rangos: **Regular**, **VIP** y **Premium**.
- Se puede consultar el historial de compras de cada cliente pulsando el ícono 👁️ en la lista.
