# 🌮 PedidosRapidos — Sistema de Gestión de Pedidos

Aplicación web para la gestión de pedidos, clientes y configuración de un negocio de comida (o similar). Está construida como una **SPA (Single Page Application) sin dependencias de servidor**: solo HTML, CSS y JavaScript vanilla, por lo que puede abrirse directamente en el navegador sin instalar nada.

---

## 🚀 Inicio rápido

1. Clona o descarga el repositorio.
2. Abre `index.html` en cualquier navegador moderno (Chrome, Firefox, Edge, Safari).
3. ¡Listo! La aplicación carga con datos de demostración precargados.

> No requiere Node.js, npm, ni servidor backend. Todo se ejecuta en el navegador.

---

## 🗂️ Estructura de archivos

```
/
├── index.html        # Punto de entrada principal y estructura del layout
├── css/
│   └── styles.css    # Estilos globales y variables de tema
└── js/
    └── app.js        # Toda la lógica de la aplicación
```

---

## 🧭 Navegación

La aplicación usa **hash routing** (`#/ruta`). Las rutas disponibles son:

| Ruta | Página |
|------|--------|
| `#/` | Dashboard |
| `#/pedidos` | Lista de pedidos |
| `#/pedidos/nuevo` | Crear nuevo pedido |
| `#/pedidos/:id` | Detalle de un pedido |
| `#/clientes` | Lista de clientes |
| `#/clientes/:id` | Detalle de un cliente |
| `#/reportes` | Reportes *(próximamente)* |
| `#/ajustes` | Configuración del negocio |

---

## 📦 Módulos de la aplicación

### 🏠 Dashboard
Vista general con métricas clave del negocio:
- Pedidos del día, total cobrado, tasa de entrega y pedidos pendientes/en proceso.
- Tabla con las operaciones del día actual (clicables para ver el detalle).

### 📋 Pedidos
Gestión completa del ciclo de vida de los pedidos:
- **Listado** con búsqueda por ID o nombre de cliente, filtros por estado (Todos / Pendiente / En Proceso / Entregado) y paginación de 10 en 10.
- **Nuevo pedido**: selección de cliente, adición de productos con cantidades, notas opcionales y cálculo automático de subtotal, IVA y total.
- **Detalle de pedido**: vista completa con posibilidad de cambiar el estado, editar o eliminar el pedido.
- **Exportar CSV**: descarga la lista de pedidos visible como archivo `.csv`.

#### Estados de un pedido
| Estado | Descripción |
|--------|-------------|
| `pendiente` | Pedido recibido, aún sin procesar |
| `en_proceso` | En preparación o camino |
| `entregado` | Completado y entregado |

### 👥 Clientes
- **Listado** con búsqueda por nombre, email o ciudad, y filtro por nivel (Regular / Premium / VIP).
- **Detalle de cliente**: historial de pedidos, gasto total, fecha del último pedido y datos de contacto.
- Los datos del cliente (total gastado, número de pedidos) se **recalculan automáticamente** al crear, editar o eliminar pedidos relacionados.

#### Niveles de cliente
| Nivel | Descripción |
|-------|-------------|
| `regular` | Cliente estándar |
| `premium` | Cliente frecuente |
| `vip` | Cliente de alto valor |

### 📊 Reportes
Sección reservada para futuros análisis y gráficos detallados. Actualmente muestra un aviso de "próximamente".

### ⚙️ Ajustes
Configuración persistente del negocio:
- Nombre del negocio, email y teléfono de contacto.
- Tasa de IVA y opción de calcularlo automáticamente en cada pedido.
- Preferencias de notificación (email / SMS).

---

## 💾 Persistencia de datos

Los datos se almacenan en el **`localStorage` del navegador** bajo las claves:

| Clave | Contenido |
|-------|-----------|
| `om_products` | Catálogo de productos |
| `om_clients` | Lista de clientes |
| `om_orders` | Todos los pedidos |
| `om_settings` | Configuración del negocio |
| `om_theme` | Preferencia de tema (claro/oscuro) |

La primera vez que se abre la aplicación, se cargan automáticamente **datos de demostración** (Taquería El Pastorcito) con 8 productos, 8 clientes y 12 pedidos de ejemplo.

> ⚠️ Los datos viven en el navegador. Si borras el localStorage o usas otro navegador/perfil, los cambios no estarán disponibles.

---

## 🎨 Interfaz y tema

- Sidebar lateral colapsable (en móvil se cierra al navegar).
- Botón en el header para alternar entre **tema claro y oscuro**. La preferencia se guarda en localStorage.
- Notificaciones tipo toast (éxito / error / info) que desaparecen automáticamente a los 4 segundos.
- Modales de confirmación para acciones destructivas (eliminar pedido).

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Uso |
|------------|-----|
| HTML5 | Estructura de la aplicación |
| CSS3 (variables) | Estilos y temas claro/oscuro |
| JavaScript ES6+ | Lógica, routing y manejo de datos |
| [Lucide Icons](https://lucide.dev) | Iconografía (cargado via CDN) |
| localStorage | Persistencia de datos en el navegador |

---

## 📁 Archivos adicionales del repositorio

Los siguientes archivos corresponden a una configuración **Next.js / React** que aún no está integrada en la versión HTML actual, pero forman parte del proyecto para una futura migración:

- `layout.tsx`, `globals.css`, `theme-provider.tsx` — Estructura base de Next.js con Tailwind CSS y shadcn/ui.
- `use-mobile.ts`, `use-toast.ts` — Hooks de React reutilizables.
- `package.json`, `tsconfig.json`, `next.config.mjs`, `postcss.config.mjs` — Configuración del entorno Next.js.
- `components.json` — Configuración de shadcn/ui (estilo New York, base neutral).

---

## 📌 Notas de desarrollo

- Los IDs de pedidos y clientes se generan con timestamp + aleatorio: `ORD-<base36timestamp><random>`.
- El IVA por defecto es del **16%** (configurable en Ajustes).
- La exportación CSV incluye BOM UTF-8 para compatibilidad con Excel en español.
- El router es client-side puro vía `window.location.hash` y el evento `hashchange`.
