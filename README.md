# 🎸 Revival of the Beast

<p align="center">
  <b>Proyecto open-source de preservación e ingeniería inversa para mantener vivo <i>Iron Maiden: Legacy of the Beast</i>.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Fase%20Experimental%20%2F%20Alpha-orange?style=flat-square" alt="Status">
  <img src="https://img.shields.io/badge/Tech-Python%20%2F%20Flask%20%2F%20Frida-blue?style=flat-square" alt="Tech Stack">
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square" alt="License">
</p>

---

## ⚡ Visión General del Proyecto

**Revival of the Beast** nace como una iniciativa para contrarrestar la obsolescencia programada y el cierre de servidores de juegos como servicio (GaaS). El objetivo principal es desacoplar el cliente original de Unity (*Iron Maiden: Legacy of the Beast*) de su infraestructura cerrada original, redirigiendo su tráfico hacia un servidor backend de control local (*Flask*) mediante instrumentación dinámica en tiempo de ejecución (*Frida*).

---

## 🗺️ Estado del Proyecto (Roadmap)

### ✅ Completado (Funcionando)
* **Redirección y Bypass de Conectividad:** Intercepción limpia de peticiones HTTP/HTTPS para desviar los dominios oficiales hacia el entorno local.
* **Estabilización del Arranque:** Supresión de bloqueos por tiempos de espera agotados (`WeakConnectionScreen`) y temporizadores fatales.
* **Mockeo del subsistema IAP:** Evasión de fallos críticos en la inicialización de la tienda y pasarela de pagos.
* **Autenticación Base y Sesión:** Inyección de variables de entorno del cliente (`PoutineManager`) y carga inicial de perfiles de usuario.

### 🟡 Parcialmente Completo (En Pruebas)
* **Sincronización de Inventarios y Personajes:** Lectura de definiciones masivas (`item_data.json`), aunque con desajustes puntuales en esquemas complejos.
* **Gestión de Eventos y Sistemas Secundarios:** Interacción básica con menús principales, aunque con excepciones aisladas en callbacks asíncronos (como el módulo de recompensas PvP/Gauntlet).
* **Acciones de Economía y Sacrificio:** Peticiones de sacrificio de personajes procesándose, pendientes de robustecer el parseo estricto de metadatos (`meta` en formato JSON).

### ❌ Pendiente / Por Desarrollar
* **Emulación de Combates (PvE / PvP):** Procesamiento de turnos, validación de daño y lógica de batallas en el servidor.
* **Gestión de Mazmorras y Campañas:** Avance por mapas, desbloqueo de niveles y entrega persistente de recompensas de misiones.
* **Persistencia Robusta de Base de Estados:** Transición de un archivo de estado plano (`state.json`) a un motor de base de datos relacional ligero (como SQLite) para concurrencia y consistencia.

---

## 💡 Próximos Pasos & Ideas No Contempladas (Bonus)

Si buscas expandir la arquitectura del proyecto más allá de simplemente "hacerlo arrancar", considera estas líneas de trabajo futuras:

1. **Panel de Administración Web (Dashboard):** 
   * Una interfaz web ligera (integrada en Flask o externa) para modificar en tiempo real las almas, fragmentos, monedas y nivel del usuario conectado sin tener que editar manualmente archivos JSON.
2. **Proxy de Captura y Replay Automático:**
   * Desarrollar un script middleware que, ante una petición de un endpoint desconocido que devuelva 500 o 404, consulte de forma inteligente un *dataset* de respuestas genéricas válidas o registre logs detallados para autocompletar JSONs faltantes.
3. **Persistencia Multi-Usuario (Soporte Multi-Player local):**
   * Migrar la estructura de `state.json` para soportar múltiples IDs de usuario mediante tokens de sesión únicos, permitiendo probar diferentes estados de cuenta (principiante, *end-game* con todo desbloqueado) sin sobreescribir datos.
4. **Mockeo de Sincronización Horaria (Time-Travel Debugging):**
   * Forzar o simular respuestas de tiempo del servidor (`currentClientUtcNow`) para probar eventos especiales temporales, mazmorras semanales o bonificaciones de inicio de sesión que el juego original bloquea por fecha.

---

## ⚠️ Aviso Legal
Este repositorio tiene fines estrictamente educativos, de investigación y de preservación de software. No está afiliado ni respaldado por Iron Maiden, Roadhouse Interactive ni Nodding Frog.
