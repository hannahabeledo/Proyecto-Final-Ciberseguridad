# Auditoría de seguridad personal

Proyecto final del Curso de Ciberseguridad de Coderhouse (octubre de 2026). Audité la seguridad de mi propia red doméstica, mi computadora y mis cuentas, clasifiqué los hallazgos por gravedad y armé un plan de mitigación con prioridades, plazos y una forma de verificar cada medida.

📄 **[Leer el informe completo](informe/informe.md)**

## Qué hice

| Área | Qué hice | Herramientas |
|---|---|---|
| Red doméstica | Descubrimiento de equipos (17 activos) y escaneo de puertos del router y la computadora, comparando escaneos SYN y Xmas | Nmap 7.98 |
| Tráfico | Captura y análisis de tráfico HTTP y HTTPS: qué queda expuesto en texto plano y qué se sigue viendo con TLS (DNS y SNI). Análisis del three-way handshake de TCP | Wireshark 4.6.9 |
| Laboratorio | Máquina virtual con hardening básico: red NAT, mínimo privilegio, permisos, actualizaciones, servicios remotos apagados y snapshots | VirtualBox, Ubuntu 26.04 LTS |
| Identidad | Bóveda de contraseñas con claves únicas de 24 caracteres (143 bits de entropía) y análisis de riesgo de cuentas con la tríada CID | KeePassXC |
| Cifrado | Contenedor cifrado con AES-256 y HMAC-SHA-512, borrado seguro de originales y copia de la cabecera | VeraCrypt |
| Respuesta a incidentes | Procedimiento ante phishing: preservación de evidencia, análisis de encabezados (SPF, DKIM, DMARC) y criterios de escalamiento | — |

## Resultados principales

- **13 hallazgos** clasificados en cuatro niveles de gravedad (alta, media, baja e informativa).
- **Riesgos altos detectados en octubre:** contraseñas de fábrica en el router y una cuenta financiera que parecía no tener doble factor. Los dos quedaron resueltos (ver Remediación).
- **Exposición de la computadora:** baja, con 2 puertos abiertos de 1000.
- **Validación de herramientas:** la detección de sistema operativo de Nmap estimó mal la versión de macOS; la corregí con el dato real del equipo y lo documenté como hallazgo.
- **Plan de mitigación** con 10 acciones priorizadas, responsable, plazo y método de verificación para cada una.

## Remediación (noviembre de 2026)

Después de la entrega apliqué el plan y repetí los escaneos para verificarlo. Detalle completo en la [sección 7 del informe](informe/informe.md#7-remediación-y-verificación-noviembre-de-2026).

| Resultado | Hallazgos |
|---|---|
| ✅ Resueltos y verificados | Contraseñas de fábrica del router, firewall de la Mac con modo encubierto, dirección Wi-Fi privada, WPS apagado (control adicional) |
| ✅ Corregidos tras verificar | La cuenta financiera y el correo ya tenían doble factor: la evaluación inicial estaba incompleta |
| 🟡 Riesgos aceptados con controles compensatorios | UPnP (se usa para juegos online), panel del router por HTTP, puerto 9090 del proveedor, red sin segmentar para IoT |

El cambio más visible está en el re-escaneo de la computadora: los 998 puertos cerrados pasaron de `closed (reset)` a `filtered (no-response)`.

## Qué aprendí

- No alcanza con correr la herramienta: comparar escaneos y verificar contra la realidad es parte del análisis.
- La seguridad se arma por capas, y los mismos principios (mínimo servicio, mínimo privilegio) sirven para una VM, un router o una computadora.
- En una red doméstica, el punto más débil no suele ser la computadora sino lo que la rodea: el router, los dispositivos IoT y cómo se manejan las cuentas.
- Una conclusión no está cerrada hasta que se verifica contra la configuración real: al remediar encontré dos hallazgos que había evaluado mal.
- No todo riesgo se elimina: algunos se aceptan, siempre que se documente por qué y qué los compensa.

## Sobre esta versión

Todas las pruebas las hice sobre equipos, redes y cuentas propias. Para publicar el informe saqué los datos que identifican mi red, mis equipos y mis cuentas: la marca y el modelo del router, el proveedor de Internet, el nombre de la red Wi-Fi, las direcciones MAC y los fabricantes asociados, y las direcciones IPv6 públicas. Las cuentas que aparecen en la bóveda de contraseñas son de prueba.

---

**Hannah Abeledo** · [LinkedIn](https://www.linkedin.com/in/hannahabeledo/)
