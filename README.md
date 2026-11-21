# BastionMCProtections 1.0.0 — prototipo para pruebas
Proyecto fuente para Purpur 1.21.11, Java 21/25. GitHub Actions genera el JAR.

## Instalación de prueba
1. Subir todos los archivos, incluida `.github/workflows/build.yml`, al repositorio privado Build-BastionMCProtections.
2. Actions > Build BastionMCProtections > ejecutar y descargar BastionMCProtections-JAR.
3. Extraer el JAR e instalarlo en un servidor de pruebas Purpur (no Velocity). Vault y un proveedor de economía para compras; WorldGuard + WorldEdit para nuevas colocaciones (habilitado por defecto); LuckPerms para límites.
4. Configurar enlace Tebex, probar compras, regiones y reinicios. No usar con público hasta superar pruebas.

## Alcance y límites de esta entrega
Código sin compilación verificada ni pruebas de ejecución en este entorno. Guarda datos en YAML mediante reemplazo atómico y copia, no SQLite. No garantiza atomicidad entre economía, inventario, bloques y disco. No usar para compras reales. Menús de miembros/listas y renombrado usan comandos; confirmación por comando, no GUI. Los avisos pendientes se entregan al siguiente OP; falta registro individual por OP. Falta completar seguridad de vehículos, pociones, dispensadores, pesca, cargas de viento, esponjas, crecimiento y otros exploits, índices espaciales, hologramas al cargar chunks, personalización total (algunos mensajes y controles internos aún fijos), administración completa, límites compartidos al dividir bases, y persistencia de entregas Tebex desconectadas. La caducidad y particiones requieren pruebas de recuperación. No subir claves ni datos de jugadores al repositorio.

## Pruebas requeridas
- Colocación de los seis niveles en world y rechazo en otros mundos, intersecciones WorldGuard, bloques normales.
- Rol visitante, confianza, codueño (máximo cuatro), propietario, vetos y expulsión, teleport de cinco segundos y cancelación; comprobar inventarios al comprar/retirar.
- Unir y dividir bases, Netherite permanente, transferencia, reinicio y corrupción de datos.
- Intentos de robo indirectos, eventos de plugins y acceso desde límites; estas pruebas son bloqueantes para producción.

Comandos: /protecciones, /protes, /prote home, /prote homes, /prote agregar a NAME, /prote remover a NAME, /prote codueño agregar a NAME, /prote codueño remover a NAME, /prote ban NAME, /prote unban NAME, /prote flags, /prote nombre NAME, /prote setspawn prote NAME, /prote resetspawn prote NAME, /prote unir NAME1 NAME2, /prote salirse de NAME, /prote transferir a NAME, /prote aceptar, /prote rechazar, /prote confirmar, /prote give NAME tipo cantidad, /prote admin bypass, /prote admin info, /prote reload.

## 1.0.1
- Contador de Carbón actualizado cada segundo en el menú; precios con separadores y color según saldo.
- /prote abre el menú; /proteunir prepara la unión; máximo 4 secciones.
- Límites de miembros 20/30/40/40; listas de cabezas para miembros, codueños y vetados; fechas persistentes cuando se conocen.
- Nombres iniciales legibles y migración de nombres automáticos antiguos; botón de spawn muestra instrucciones.
- Los menús de listas son de consulta; gestionar altas/bajas mediante comandos originales.
- Conserva data.yml y copia de respaldo. Guarda el config.yml anterior y combina tus personalizaciones con el nuevo config.yml incluido. No borres los datos. Si una base antigua supera un límite nuevo no se expulsan miembros automáticamente.
- Validación de YAML realizada; compilación y pruebas en Purpur pendientes.

## 1.0.2
Los hologramas de bases nuevas muestran `/prote nombre NAME` hasta renombrarlas. Ajustable en `hologram.unnamed-name`. Conserva nombres internos únicos para comandos y datos; no requiere borrar data.yml. Los nombres antiguos con identificador hexadecimal se migran; los nombres personalizados existentes se conservan. Compilación y pruebas en servidor pendientes.


## 1.0.3: Correccion de limites de particulas
- Corrige el chequeo de la celda exterior que ocultaba parte del perimetro.
- Emite columnas de particulas a la altura del espectador en tres niveles y sin mostrar bordes interiores de secciones unidas.
- Opciones nuevas en `particles`: `size` y `range`. Los valores ausentes tienen defaults incorporados.
- Los limites solo son visibles por jugadores situados dentro de la base, con la flag `borders` activada.
- Para aplicar ajustes al intervalo de actualizacion de particulas se requiere reinicio (el periodo se fija en onEnable).

## 1.0.4: bordes y diagnóstico
- Pared de partículas de 7 bloques de alto (configurable con `particles.height`), partículas forzadas al cliente.
- `/prote testborde` dibuja un círculo de partículas a 3 bloques del jugador para diagnosticar la visibilidad.
- Los bordes solo se envían a jugadores dentro de una base que tenga la flag `borders` activada.
- Prueba con Minecraft Opciones > Video > Partículas: Todas.

## Correcciones 1.0.5
- Los hologramas vuelven a generarse cuando carga el chunk de una protección y en el arranque diferido.
- El teletransporte de /protes precarga el chunk de destino para que funcione también desde spawn si hay destino seguro.
- Si otro plugin cancela el teletransporte, aparece un mensaje y se registra una advertencia en consola.
- Los mundos permitidos en config controlan la COLOCACIÓN de protecciones, no la apertura de /protes.
- La versión fuente no ha sido compilada en este entorno: generar JAR con GitHub Actions y probar en una copia del servidor.
