# 💊 Sistema Farmacia — Modernización Arquitectónica SOLID
 
Sistema de gestión de farmacia en C# / .NET, intervenido siguiendo los cinco principios SOLID a partir de un diagnóstico completo del código original (AS-IS → TO-BE).
 
> 🎥 Video de sustentación: **https://youtu.be/I7SfKSL7dZ8**
 
---
 
## 👥 Equipo y roles
 
Cada persona sostuvo un rol técnico fijo durante todo el análisis, el diseño y la sustentación:
 
| Rol | Responsable | Responde por |
|---|---|---|
| 🧩 **Arquitecta de dominio** | Natalia Giraldo Morales | Responsabilidades y límites de cada clase (SRP), modelo del dominio, jerarquías de herencia y su validez frente a LSP. |
| 🔗 **Arquitecta de dependencias** | Carolina Ramírez Lotero | Mapa de dependencias, abstracciones (interfaces), inversión e inyección de dependencias, composition root (DIP, ISP). |
| ✅ **Ingeniera de comportamiento** | María Alexandra Jiménez Suárez | Pruebas de caracterización, evidencia de que la conducta observable se preservó, escenarios de ejecución del programa principal. |
| 🗂️ **Integrador y evidencia** | Juan José Álvarez Restrepo | Consistencia diagrama–código, estructura del entregable, bitácora de uso de IA, métricas antes/después. |
 
---
 
## 🚀 Cómo ejecutar el proyecto
 
### Requisitos previos
 
- [.NET SDK 8.0](https://dotnet.microsoft.com/download/dotnet/8.0) o superior instalado.
- Verifica tu versión con:
```bash
  dotnet --version
```
 
### 1. Clonar el repositorio
 
```bash
git clone https://github.com/Mariajimenez16/Farmacia.git
```
 
### 2. Entrar hasta el proyecto ejecutable
 
⚠️ **Importante:** el proyecto que se ejecuta (`AppFarmaciaConsola`) está anidado varios niveles dentro del repositorio. Tienes que entrar exactamente hasta esta ruta antes de correr el comando:
 
```
SolucionFarmacia V2 1/SolucionFarmacia V2/SolucionFarmacia V1/SolucionFarmacia/AppFarmaciaConsola
```
 
**En Windows (PowerShell / CMD):**
```powershell
cd "SolucionFarmacia V2 1\SolucionFarmacia V2\SolucionFarmacia V1\SolucionFarmacia\AppFarmaciaConsola"
```
 
**En macOS / Linux:**
```bash
cd "SolucionFarmacia V2 1/SolucionFarmacia V2/SolucionFarmacia V1/SolucionFarmacia/AppFarmaciaConsola"
```
 
> 💡 Tip: si te da pereza escribir la ruta completa, usa autocompletado con `Tab` después de escribir `cd So` — PowerShell y bash la completan solos.
 
### 3. Ejecutar
 
```bash
dotnet run
```
 
Deberías ver algo como esto:
 
```
PS C:\...\SolucionFarmacia V2 1\SolucionFarmacia V2\SolucionFarmacia V1\SolucionFarmacia\AppFarmaciaConsola> dotnet run
 
==============================
      SISTEMA FARMACIA
==============================
1. Ver productos
2. Ver clientes
3. Buscar producto
4. Registrar venta
5. Acumular puntos
6. Ver alertas
7. Salir
```
 
Si ves ese menú, el sistema quedó corriendo correctamente — incluyendo la carga de las tres familias de producto (medicamentos, cosméticos y comestibles) desde sus respectivos archivos de texto.
 
---
 
## 🗃️ Datos de entrada
 
El programa carga automáticamente estos archivos al iniciar (ya incluidos en el repositorio, dentro de `AppFarmaciaConsola/`):
 
| Archivo | Contenido |
|---|---|
| `productos.txt` | Medicamentos |
| `cosmeticos.txt` | Cosméticos (SC-1) |
| `comestibles.txt` | Comestibles (SC-1) |
| `clientes.txt` | Clientes registrados |
| `usuarios.txt` | Usuarios del sistema |
 
---
 
## 🏗️ Qué cambió respecto al sistema original
 
Este repositorio contiene la versión **TO-BE**, resultado de aplicar SRP, OCP, LSP, DIP e ISP sobre hallazgos reales documentados en la Fase 1. Un resumen rápido:
 
- Los servicios (`ServicioProducto`, `ServicioCliente`, `ServicioUsuario`) ya no leen archivos directamente ni crean sus propios eventos — reciben todo por inyección de dependencias.
- La autenticación se separó a una clase propia, `ServicioAutenticacion`.
- Cosméticos y comestibles se agregaron como nuevas familias de producto **sin modificar** `ServicioProducto` — cada familia tiene su propio repositorio, todos implementando la misma interfaz.
- El comportamiento observable del sistema (lo que ves en consola) se mantuvo idéntico al original en todo momento.
El detalle completo — diagrama AS-IS, diagrama TO-BE con convención de color por principio, inventario de hallazgos y los 6 ADR con alternativas descartadas.
 
---
 
## 🎥 Video de sustentación
 
📺 **https://youtu.be/I7SfKSL7dZ8**
 
En el video se recorre: el sistema AS-IS y los puntos de dolor priorizados, los hallazgos propios y el falso positivo que refutamos, el diagrama TO-BE decisión por decisión, ejecución en vivo con la métrica antes/después, y la deuda técnica que dejamos consciente.
 
