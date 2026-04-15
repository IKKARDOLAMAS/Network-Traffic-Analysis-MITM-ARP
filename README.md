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
```bash
sudo sysctl -w net.ipv4.ip_forward=1```



