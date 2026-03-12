# ☕ Sistema de Gestión de Inventario - Cafetería

Sistema completo para gestionar inventario, ventas y turnos de una cafetería, con almacenamiento en la nube usando Supabase.

---

## 🚀 Inicio Rápido (5 Minutos)

### 1️⃣ Configura Supabase

1. Ejecuta el SQL en tu proyecto de Supabase (archivo `/supabase-setup.sql`)
2. Crea el bucket `cafeteria-videos` en Storage
3. Copia tus credenciales (Project URL + anon key)

### 2️⃣ Configura el Código

Edita `/src/lib/supabase.ts` y reemplaza:

```typescript
const SUPABASE_URL = 'https://tu-proyecto.supabase.co';
const SUPABASE_ANON_KEY = 'eyJhbGciOi...';
```

### 3️⃣ Despliega

```bash
npm install -g vercel
vercel
```

### 4️⃣ Abre en la Tablet

1. Ve a la URL que te dio Vercel
2. Añade a pantalla de inicio
3. ¡Listo!

**¿Primera vez?** Lee → `/INICIO_RAPIDO.md` (guía completa paso a paso)

---

## 📚 Documentación

| Archivo | Descripción |
|---------|-------------|
| **[INICIO_RAPIDO.md](INICIO_RAPIDO.md)** | ⚡ Comienza aquí - 5 minutos |
| **[ARCHIVOS_A_EDITAR.md](ARCHIVOS_A_EDITAR.md)** | 📝 Qué archivos debes editar |
| **[INSTRUCCIONES_SUPABASE.md](INSTRUCCIONES_SUPABASE.md)** | 📖 Instrucciones completas de Supabase |
| **[COMANDOS_DEPLOY.md](COMANDOS_DEPLOY.md)** | 🚀 Comandos para desplegar |
| **[CHECKLIST.md](CHECKLIST.md)** | ✅ Lista de verificación |
| **[README_IMPLEMENTACION.md](README_IMPLEMENTACION.md)** | 📊 Resumen completo del sistema |
| **[supabase-setup.sql](supabase-setup.sql)** | 🗄️ Script SQL para Supabase |

---

## ✨ Características

### 🛒 Gestión de Ventas
- Interfaz intuitiva para registro de ventas
- Cálculo automático de totales
- Contador de dinero en caja en tiempo real
- Historial completo de transacciones

### 📦 Control de Inventario
- Stock individual y grupos compartidos
- Sistema de reabastecimiento automático
- Alertas de stock bajo
- Descuento automático de complementos (Maruchan)

### 🔄 Gestión de Turnos
- Apertura/cierre de cafetería con confirmación
- Registro de dinero inicial y final
- Reportes de diferencias
- Historial de todos los turnos

### 🎥 Personalización
- Subida de videos personalizados
- Almacenamiento permanente en Supabase
- Reproducción automática en pantalla de inicio

### 🔐 Panel Administrativo
- Protegido con clave (1062000)
- Gestión completa de inventario
- Ajuste de precios y cantidades
- Reportes de ventas y turnos

---

## 🏗️ Estructura del Proyecto

```
📦 cafeteria-sistema/
│
├── 📂 src/
│   ├── 📂 lib/
│   │   ├── supabase.ts           # ✏️ Configuración de Supabase (EDITAR AQUÍ)
│   │   └── supabase-sync.ts      # Funciones de sincronización
│   │
│   └── 📂 app/
│       ├── App.tsx                # Componente principal
│       ├── 📂 components/
│       │   ├── SalesScreen.tsx   # Pantalla de ventas
│       │   ├── AdminPanel.tsx    # Panel administrativo
│       │   ├── VideoUploader.tsx # Subida de videos
│       │   └── ...               # Otros componentes
│       │
│       └── 📂 types/
│           └── inventory.ts       # Definiciones de tipos
│
├── 📄 Documentación (lee estos archivos)
├── 📄 supabase-setup.sql         # SQL para crear tablas
└── 📄 package.json                # Dependencias
```

---

## 💾 Base de Datos (Supabase)

### Tablas

| Tabla | Descripción |
|-------|-------------|
| `products` | Productos del inventario |
| `stock_groups` | Grupos de stock compartido |
| `sales` | Registro de ventas |
| `shifts` | Registro de turnos |
| `cafeteria_state` | Estado actual de la cafetería |
| `configuration` | Configuraciones del sistema |

### Storage

| Bucket | Descripción |
|--------|-------------|
| `cafeteria-videos` | Videos de pantalla de inicio |

---

## 🎯 Productos y Categorías

### 🍜 Maruchan ($30)
- Camarón, Camarón Pikín, Camarón Habanero, Pollo
- Incluye: Tenedor + Sobre de galletas saladitas

### 🥔 Papitas ($25) - Stock Compartido
- Chetos Naranjas, Chetos Flaming Hot
- Ruffles, Sabritas, Rancheritos, Doritos
- Reabastecimiento: 50 unidades por paquete

### ☕ Capuchinos ($25)
- Normal, Moka, Vainilla, Crema Irlandesa, Chocolate

### 🍪 Galletas, Chocolates y Dulces
- Galletas ($20): Príncipes, Trikitrakes, Plativolos - Stock Compartido (30 unidades)
- Chocolate Canasta ($5)
- Pingüinos y Gansitos ($15)
- Galletas Saladitas Extra ($5)

---

## 🔧 Tecnologías

- **Frontend:** React + TypeScript
- **Estilos:** Tailwind CSS
- **Backend:** Supabase (PostgreSQL + Storage)
- **Build:** Vite
- **UI:** Radix UI + Custom Components
- **Notificaciones:** Sonner
- **Íconos:** Lucide React

---

## 📱 Uso del Sistema

### Apertura de Cafetería (Inicio del día)

1. Presionar "Abrir Cafetería"
2. Revisar inventario en el modal de confirmación
3. Ingresar dinero de cambio inicial
4. Confirmar
5. ✅ Sistema registra hora, stock y dinero

### Registro de Ventas

1. Seleccionar productos desde el menú
2. Ajustar cantidades con botones + / -
3. Presionar "Completar Venta"
4. ✅ Se actualiza: stock, dinero en caja, historial

### Entrega de Turno

1. Presionar "Entregar Turno"
2. Ingresar dinero reportado en caja
3. Revisar diferencias (esperado vs. reportado)
4. Confirmar
5. ✅ Se registra el turno en Supabase

### Cierre de Cafetería (Hacer Corte)

1. Presionar "Hacer Corte"
2. Ingresar dinero que se deja como cambio
3. Confirmar
4. ✅ Se cierra cafetería, se registra corte, se reinicia caja

### Panel Administrativo

1. Presionar ⚙️ (esquina superior derecha)
2. Ingresar clave: **1062000**
3. Acceder a:
   - Gestión de inventario
   - Reportes de ventas
   - Historial de turnos
   - Subida de videos
   - Configuración de precios

---

## 🌐 Despliegue

### Vercel (Recomendado)

```bash
npm install -g vercel
vercel                    # Primera vez
vercel --prod            # Actualizar
```

### Netlify

```bash
npm install -g netlify-cli
netlify login
npm run build
netlify deploy --prod
```

### Build Local

```bash
npm run build            # Genera carpeta /dist
```

---

## 🔍 Sincronización de Datos

El sistema usa una estrategia de **doble backup**:

1. **localStorage** (navegador) → Cache rápido
2. **Supabase** (nube) → Fuente de verdad

### Flujo de Datos

```
Acción del Usuario
       ↓
   App.tsx
       ↓
   ├─→ localStorage (inmediato)
   └─→ Supabase (segundo plano)
```

### Carga Inicial

```
Al abrir la app
       ↓
   ¿Existe en Supabase?
       ├─→ Sí: Cargar de Supabase
       └─→ No: Cargar de localStorage
              └─→ Si está vacío: Datos iniciales
```

---

## ⚙️ Configuración

### Credenciales de Supabase

Edita `/src/lib/supabase.ts`:

```typescript
const SUPABASE_URL = 'https://tu-proyecto.supabase.co';
const SUPABASE_ANON_KEY = 'eyJhbGciOi...';
```

### Variables de Entorno (Opcional)

Crea `.env.local`:

```env
VITE_SUPABASE_URL=https://tu-proyecto.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOi...
```

---

## 🐛 Solución de Problemas

### "SUPABASE NO CONFIGURADO"

- Edita `/src/lib/supabase.ts` con tus credenciales
- Guarda el archivo
- Reconstruye: `npm run build`
- Redesplega: `vercel --prod`

### No se guardan las ventas

- Verifica que las tablas existan en Supabase
- Verifica las políticas de acceso (deben permitir INSERT)
- Revisa la consola del navegador (F12) para errores

### No se suben videos

- Verifica que el bucket `cafeteria-videos` exista
- Verifica que sea público
- Verifica las políticas del bucket (permitir INSERT)

---

## 📊 Características Especiales

### Lógica de Maruchan

Al vender 1 Maruchan, se descuentan automáticamente:
- 1x Maruchan del inventario
- 1x Tenedor
- 1x Sobre de galletas saladitas

### Stock Compartido

- **Papitas:** 6 variedades comparten 1 stock común
- **Galletas:** 3 variedades comparten 1 stock común
- Al reabastecer, se agregan al pool compartido
- Cualquier venta descuenta del mismo pool

---

## 💰 Costo

- ✅ **Frontend:** Gratis (Vercel/Netlify)
- ✅ **Backend (Supabase):** Gratis hasta:
  - 500 MB base de datos
  - 1 GB almacenamiento
  - 50,000 usuarios activos/mes

**Para una cafetería pequeña, el plan gratuito es más que suficiente.**

---

## 🔐 Seguridad

- Clave administrativa: **1062000** (puedes cambiarla en `LoginScreen.tsx`)
- Datos en Supabase con Row Level Security
- Sin autenticación de usuarios (sistema de uso interno)

---

## 📞 Soporte

### Logs del Sistema

Presiona **F12** en el navegador para ver:
- ✅ Mensajes de sincronización exitosa
- ❌ Errores de conexión
- ⚠️ Advertencias de configuración

### Verificar Datos en Supabase

1. Ve a [app.supabase.com](https://app.supabase.com)
2. Selecciona tu proyecto
3. **Table Editor** → Ver datos de las tablas
4. **Storage** → Ver archivos subidos

---

## 🎓 Capacitación del Personal

Proporciona a tu equipo:
- Acceso a la tablet con el ícono de la app
- Clave administrativa: **1062000**
- Instrucciones básicas:
  - Cómo abrir cafetería
  - Cómo hacer ventas
  - Cómo entregar turnos
  - Cómo hacer corte

---

## 📄 Licencia

Este proyecto es de uso privado para tu cafetería.

---

## 🎉 ¡Listo para Usar!

Tu sistema está completo y funcionando. 

**Próximos pasos:**
1. Lee `/INICIO_RAPIDO.md` si es tu primera vez
2. Configura Supabase
3. Despliega en Vercel
4. Configura la tablet
5. ¡Empieza a vender! ☕

**¿Necesitas ayuda?** Revisa los archivos de documentación en la raíz del proyecto.

---

Creado con ❤️ para tu cafetería
