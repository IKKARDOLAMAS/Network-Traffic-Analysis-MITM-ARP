# 🛡️ PoC: Análisis de Intercepción de Red (Man-in-the-Middle)

## 📝 Descripción del Proyecto
Esta Prueba de Concepto (PoC) demuestra cómo un atacante puede posicionarse entre una víctima y el router (Gateway) utilizando **ARP Poisoning** para interceptar y analizar el tráfico de red en tiempo real.

## 🔬 Escenario del Laboratorio
* **Atacante:** Kali Linux (IP: 192.168.1.2) - Ejecutando Ettercap 0.8.4.
* **Víctima:** Dispositivo portátil físico (IP: 192.168.1.7).
* **Servidor Local:** Servidor HTTP en Python corriendo en la víctima para simular tráfico de Capa 7.
* **Red:** Configuración de Adaptador Puente (Bridge) para comunicación directa en Layer 2.

## 🛠️ Ejecución Técnica

### Paso 1: Configuración del Kernel
Se habilitó el reenvío de paquetes IP para permitir que el tráfico de la víctima fluya a través del atacante sin interrumpir la conexión:

```bash```
```sudo sysctl -w net.ipv4.ip_forward=1```

### Paso 2: Envenenamiento ARP (ARP Spoofing)
Se ejecutó un ataque bidireccional para engañar las tablas ARP de la víctima y del Gateway:

Target 1: 1xx.xxx.x.1 (Router)

Target 2: 1xx.xxx.x.7 (Víctima)

### Paso 3: Análisis de Resultados
A pesar de la protección de los navegadores modernos contra la visualización de texto plano en ciertos flujos, se confirmó el éxito del ataque mediante las métricas de Forwarded Packets en Ettercap:

Paquetes Reenviados: +1400 paquetes.

Tráfico Procesado: ~325,000 bytes interceptados.

### 🚨 Lecciones Aprendidas
Importancia del Cifrado: El tráfico HTTP es vulnerable a la disección, mientras que HTTPS protege el contenido de la Capa 7 incluso si la red es comprometida.

Seguridad de Red: La importancia de implementar Static ARP o Port Security en switches para evitar ataques de suplantación.

Kernel Tuning: El rol crítico del ip_forwarding en ataques de interceptación.
