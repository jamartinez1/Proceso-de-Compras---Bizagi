# 🛒 Proceso de Compras - Bizagi

Este repositorio contiene la implementación de un **proceso de compras** desarrollado en **Bizagi Studio (v11.2.5)**, como parte de una prueba técnica.

---

## 📂 Contenido del repositorio
- `ProcesoComprasMAXI.bex` → Exportación completa del proyecto en Bizagi.  
- `ProcesoComprasMAXI.bdex` → Datos de prueba (productos, proveedores, sucursales).  
- `ProcesoComprasMAXI_Documentacion.pdf` → Documento con el diagrama BPMN del proceso.  
- `README.md` → Este archivo.

---

## 📝 Descripción general del proceso
El flujo implementado refleja un ciclo de **solicitud y aprobación de compras**, con validación de stock, aprobación, selección de proveedores e integración con un servicio web para la generación de órdenes de compra.

### Principales actividades
1. **Recepción de la solicitud en sucursal**  
2. **Creación de solicitud de compra** con detalle de productos.  
3. **Validación de stock** por parte de inventario.  
4. **Aprobación o rechazo** por supervisores.  
5. **Envío a proveedores y recepción de propuestas**.  
6. **Selección del mejor proveedor**.  
7. **Generación de orden de compra vía Web Service**.  
8. **Ejecución y validación final de la compra**.

---

## 🛠 Modelo de datos
El modelo incluye las siguientes entidades principales:

- **Sucursal** → Una sucursal puede generar múltiples solicitudes de compra.  
- **SolicitudCompra** → Cabecera de la solicitud de compra.  
- **SolicitudLineas** → Detalle de productos solicitados en cada solicitud.  
- **Producto** → Catálogo de productos con stock y características.  
- **Proveedor** → Lista de proveedores disponibles.  
- **OrdenCompra** → Generada automáticamente tras la aprobación, relacionada con el proveedor.  

Relaciones clave:
- `Sucursal 1 → * SolicitudCompra`  
- `SolicitudCompra 1 → * SolicitudLineas`  
- `SolicitudLineas * → 1 Producto`  
- `OrdenCompra * → 1 Proveedor`

---

## ▶️ Ejecución
1. **Importar el proyecto** (`.bex`) en Bizagi Studio.  
3. Iniciar el proceso desde el **Portal de Trabajo de Bizagi**.  
4. Seguir las diferentes rutas del proceso (aprobación, rechazo, cancelación, compra).  

---

## 🌐 Integración
Se configuró un **conector SOAP** de ejemplo contra el servicio público:  
[`https://legacy.bizagi.com/OfficeSupplyWS/OfficeService.asmx`](https://legacy.bizagi.com/OfficeSupplyWS/OfficeService.asmx)  
El objetivo es simular la **generación automática del número de orden de compra**.

---

## ⚠️ Notas
- Algunas reglas de negocio quedaron en desarrollo parcial.  
- El proceso y los formularios cubren los **requisitos principales de la prueba**.  
- El modelo es extensible: se pueden añadir más atributos y validaciones según la necesidad.  

---

## 📌 Autor
Prueba técnica desarrollada por **Jhon Martinez**  
