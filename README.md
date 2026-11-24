# Auditoría de seguridad personal

Este fue mi proyecto final del curso de Ciberseguridad de Coderhouse, en octubre de 2026. La consigna era hacer un "informe de salud digital", y lo hice sobre lo que tengo a mano: la red de mi casa, mi computadora y mis cuentas.

Escaneé la red con Nmap, analicé mi propio tráfico con Wireshark, armé una máquina virtual con hardening básico y usé KeePassXC y VeraCrypt para contraseñas y cifrado. Con todo eso clasifiqué 13 hallazgos por gravedad y armé un plan para corregirlos.

En noviembre volví sobre el trabajo, apliqué el plan y repetí los escaneos para ver si los cambios funcionaban. Eso está en la sección 7.

[Informe completo](informe/informe.md)

## Herramientas

- **Nmap 7.98:** descubrimiento de la red y escaneos SYN y Xmas sobre el router y la computadora.
- **Wireshark 4.6.9:** captura de tráfico HTTP y HTTPS, consultas DNS y three-way handshake de TCP.
- **VirtualBox y Ubuntu 26.04 LTS:** laboratorio con red NAT, usuario sin privilegios, permisos, actualizaciones y snapshots.
- **KeePassXC:** bóveda con contraseñas únicas de 24 caracteres.
- **VeraCrypt:** contenedor cifrado con AES-256, borrado seguro de originales y copia de la cabecera.

## Qué encontré y qué pasó después

Lo más grave era el router, que seguía con las contraseñas de fábrica impresas en la etiqueta. Las cambié y comprobé que las viejas ya no funcionan.

También había marcado como riesgo alto que mi cuenta del banco no tenía doble factor. Cuando fui a activarlo, vi que ya estaba activo para operar: me había fijado solo en el inicio de sesión. Con el correo me pasó parecido. Lo dejé documentado como corrección, porque me parece tan importante como lo que sí encontré bien.

En la computadora activé el firewall con modo encubierto y la dirección Wi-Fi privada. En el re-escaneo se nota la diferencia: los 998 puertos cerrados pasaron de responder con un rechazo (`closed`) a no responder nada (`filtered`).

Hay cosas que decidí no cambiar, como UPnP, que en casa se usa para jugar online. Las dejé registradas como riesgos aceptados, con lo que hice para compensarlos.

## Lo que me llevo

- Nmap se equivocó con la versión de macOS y yo me equivoqué con el banco. En los dos casos, lo que lo resolvió fue ir a ver la configuración real.
- Los mismos principios que apliqué en la máquina virtual (no tener servicios de más, no usar permisos de administrador para todo) sirven igual para un router o una Mac.
- En una casa, lo más débil no suele ser la computadora sino lo que la rodea: el router, los aparatos inteligentes y cómo uno maneja sus cuentas.

## Sobre esta versión

Todas las pruebas las hice sobre equipos, redes y cuentas propias. Antes de publicarlo saqué lo que identifica mi red y mis cuentas: el modelo del router, el proveedor de Internet, el nombre del Wi-Fi, las direcciones MAC, las IPv6 públicas y el nombre del banco. Las cuentas que aparecen en la bóveda de KeePassXC son inventadas.

Hannah Abeledo · [LinkedIn](https://www.linkedin.com/in/hannahabeledo/)
