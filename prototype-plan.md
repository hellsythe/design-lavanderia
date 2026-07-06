# Plan de prototipo — LavanderPro

## Resumen de intención
Crear las pantallas de producto clave para LavanderPro: **autenticación** (login y registro) y **punto de venta (POS)** para levantar nuevos pedidos. Cada pantalla debe verse como parte del mismo producto, usar el design system activo (Github Dashboard / LavanderPro) y funcionar como archivo HTML independiente y responsivo.

## Audiencia
- Dueño o administrador de una lavandería comercial/industrial.
- Usuario que accede principalmente desde escritorio, tablet o móvil.

## Plataforma
Responsive web. Cada pantalla es un archivo HTML independiente (`login.html`, `register.html` y `pos.html`) siguiendo la regla *screen-file-first* del proyecto.

## Dirección visual
Usar el design system activo **Github Dashboard Design System / LavanderPro**:
- Fondo de página: `#F0F4F8` (`--bg`).
- Tarjeta/superficie: `#FFFFFF` (`--surface`) con borde `#E1E8F0` (`--border`).
- Texto principal: `#1A2332` (`--fg`); texto secundario: `#64748B` (`--muted`).
- Acento: teal `#0D9488` (`--accent`) para botón primario, focus ring y estados activos.
- Tipografía: Public Sans (400/500/600/700) con fallbacks del sistema.
- Radio de tarjeta: `10px`; inputs y botones: `7–8px`.
- Sin animaciones de entrada; solo transiciones de estado (`:hover`, `:focus`, `:active`).

## Pantallas

### 1. `login.html` — Iniciar sesión
**Objetivo:** Permitir al usuario acceder al dashboard con credenciales existentes.

**Campos del formulario:**
- Correo electrónico (`type="email"`, required).
- Contraseña (`type="password"`, required).

**Acciones:**
- Botón primario: **Iniciar sesión**.
- Link secundario: **¿Olvidaste tu contraseña?** (placeholder de flujo futuro).
- Link a registro: **Crear cuenta**.

**Estados:**
- Default: formulario limpio, botón habilitado.
- Focus: ring de `--accent` en inputs y botones.
- Loading: botón muestra indicador y se deshabilita.
- Error: mensaje bajo el campo afectado o mensaje global; borde del input en `--danger`.
- Success: redirección simulada al dashboard (`index.html`) o mensaje de éxito breve.

### 2. `register.html` — Crear cuenta
**Objetivo:** Registrar un nuevo usuario con los datos mínimos solicitados.

**Campos del formulario:**
- Nombre completo (`type="text"`, required).
- Correo electrónico (`type="email"`, required).
- Contraseña (`type="password"`, required).

**Acciones:**
- Botón primario: **Crear cuenta**.
- Link a login: **Ya tengo una cuenta**.

**Estados:**
- Default, focus, loading, error y success, igual que login.
- Validación básica: email con formato válido, contraseña no vacía, nombre no vacío.
- Success: mensaje "Cuenta creada" y redirección simulada a `login.html` o `index.html`.

### 3. `pos.html` — Levantar pedido
**Objetivo:** Permitir al dueño/administrador registrar un nuevo pedido de lavandería de forma rápida desde un punto de venta.

**Campos y secciones del formulario:**
- **Cliente:** campo de búsqueda con autocomplete (`input type="search"`) que permite seleccionar un cliente existente o dejar indicado que es nuevo.
- **Servicios:** lista de servicios seleccionables (Lavado Industrial, Lavado + Secado, Lavado Delicado, Esterilizado, Lavado + Planchado) con selector de cantidad y precio unitario.
- **Peso total (kg):** input numérico (`type="number"`) para capturar el peso de la carga.
- **Fecha/hora de entrega estimada:** input `datetime-local` prellenado con una hora razonable (por ejemplo, +24 h).
- **Notas:** textarea opcional para instrucciones especiales.
- **Resumen:** panel lateral o inferior que muestra subtotal, total estimado y botón de guardar.

**Acciones:**
- Botón primario: **Guardar pedido**.
- Botón secundario: **Cancelar** (vuelve al dashboard).
- Link/botón para agregar otro servicio.

**Estados:**
- Default: formulario limpio con valores por defecto.
- Focus: ring de `--accent` en inputs y botones.
- Loading: botón deshabilitado con spinner mientras se "guarda".
- Error: mensajes de validación si faltan cliente, servicios o peso.
- Success: mensaje de confirmación con el número de orden generado y redirección a `index.html` o a la pantalla de pedidos.

## Estructura de layout

### Autenticación (`login.html` / `register.html`)
- Contenedor centrado (`min-height: 100vh`, flex/grid centrado).
- Tarjeta blanca con borde y sombra sutil del design system.
- Dentro de la tarjeta:
  1. Logo/ícono de LavanderPro + nombre + badge "Industrial".
  2. Título de pantalla (ej. "Iniciar sesión").
  3. Formulario con labels y inputs.
  4. Botón primario a ancho completo.
  5. Link secundario centrado debajo del botón.
- Footer opcional: copyright o versión del producto.

### POS (`pos.html`)
- Layout de una o dos columnas según ancho de pantalla:
  - **Escritorio/tablet:** columna izquierda (2fr) con el formulario de cliente + servicios + detalles; columna derecha (1fr) con el resumen y totales.
  - **Móvil:** una sola columna con el resumen como card pegajosa en la parte inferior o al final del formulario.
- Topbar simplificado con título "Nuevo pedido", botón de cancelar y botón de guardar.
- Sin sidebar para mantener el foco en la tarea (solo topbar + formulario).
- Tarjetas de servicio seleccionables con borde, cantidad y precio.

## Componentes requeridos
- **Input de texto/contraseña:** estilo del design system (`border: 1px solid var(--border)`, `border-radius: 7px`, `background: var(--surface-2)` en reposo, `--surface` en focus).
- **Toggle de visibilidad de contraseña:** ícono de ojo dentro del input (solo autenticación).
- **Botón primario:** fondo `--accent`, texto blanco, `border-radius: 8px`, estado `:active` con `translateY(1px)`.
- **Botón/link secundario:** texto `--accent` o `--muted` según jerarquía.
- **Mensaje de error:** fondo `--danger-soft`, texto `--danger`, `border-radius: 8px`.
- **Spinner de carga:** SVG simple dentro del botón.
- **Search input con autocomplete (POS):** input de búsqueda que filtra clientes existentes y permite seleccionar; estilo `search-input` del design system.
- **Tarjeta de servicio seleccionable (POS):** card con borde, título, descripción corta, precio unitario y stepper de cantidad; estado activo con borde `--accent` y fondo `--accent-soft`.
- **Stepper de cantidad (POS):** botones `−` / `+` y campo numérico central; mínimo 0, máximo razonable (ej. 99).
- **Panel de resumen (POS):** card lateral/inferior con subtotal, lista de servicios agregados y total estimado.

## Reglas de interacción
- `Enter` en cualquier input envía el formulario (autenticación).
- Validación al enviar; no bloquear con validación en tiempo real agresiva.
- Contraseña se puede mostrar/ocultar con el toggle.
- En error, mover foco al primer campo inválido.
- En éxito, simular redirección con `setTimeout` o cambio de `window.location.hash`.
- Soporte para `prefers-reduced-motion`.

### POS específicas
- Al seleccionar un servicio, su cantidad por defecto es 1 y se agrega al resumen.
- Al cambiar cantidad o deseleccionar un servicio, el total se recalcula en tiempo real.
- El cliente debe existir en la lista o marcarse como "nuevo"; si no se selecciona ninguno, mostrar error.
- El peso es obligatorio y debe ser mayor a 0.
- La fecha de entrega estimada se prellena con +24 h y se puede editar.
- Al guardar, simular una llamada de red (spinner + delay) y luego mostrar el número de orden generado.
- El botón **Cancelar** regresa al dashboard sin guardar.

## Modelo de datos
```js
// Login
{ email: string, password: string }

// Register
{ name: string, email: string, password: string }

// POS order
{
  client: { id?: string, name: string, isNew: boolean },
  services: [{ serviceId: string, name: string, qty: number, unitPrice: number }],
  weightKg: number,
  estimatedDelivery: string, // ISO datetime
  notes: string,
  total: number
}
```

## Criterios de aceptación
- [ ] Las páginas `login.html`, `register.html` y `pos.html` son archivos HTML independientes y responsivos.
- [ ] Usan únicamente la paleta y tipografía del design system activo.
- [ ] No incluyen animaciones de entrada.
- [ ] Los formularios de autenticación tienen validación real, toggle de contraseña y mensajes de error visibles.
- [ ] La vista POS permite seleccionar cliente, agregar servicios con cantidad, ingresar peso y ver el total en tiempo real.
- [ ] La vista POS valida campos obligatorios antes de guardar y muestra mensajes de error.
- [ ] Los estados de carga deshabilitan el botón y muestran indicador.
- [ ] El copy está en español (es-MX) y es específico del producto.
- [ ] Los enlaces entre login, registro y dashboard funcionan; el POS tiene botón de cancelar que regresa al dashboard.

## Siguiente paso
Revisa este plan actualizado. Una vez aprobado, generaré `pos.html` (y ajustaré `login.html` / `register.html` si es necesario) con el design system de LavanderPro aplicado.
