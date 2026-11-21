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
