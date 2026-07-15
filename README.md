# kuwaiba-ftth-testing
Entorno de contenedores Docker y documentación de testeo para el inventario georreferenciado de red FTTH usando Kuwaiba.
# Informe de Testeo y Avance en Kuwaiba - Infraestructura FTTH Arequipa

### 📊 Estado del Testeo: Exitoso (Fase de Modelado Físico y OSP)
En esta fase de pruebas, se ha desplegado con éxito una instancia de **Kuwaiba v2.1.1** alojada localmente sobre un entorno virtualizado Linux (con acceso a internet vía NAT). Los hitos logrados en el testeo actual son:

* **Creación del Árbol de Inventario Geográfico:** Se estructuró la jerarquía lógica del país dentro del sistema: `America` -> `peru` -> `Arequipa` -> `Nodo_Central_Arequipa`.
* **Georreferenciación de Activos:** Se configuraron con éxito las coordenadas geográficas reales del nodo principal en el distrito de Cayma/Yanahuara, Arequipa (Latitud: `-16.345...`, Longitud: `-71.545...`).
* **Inicialización del Visor de Planta Externa (Outside Plant - OSP):** Se validó el motor de mapas OpenStreetMap integrado en Kuwaiba y se creó con éxito la vista geográfica (`Outside Plant View`) exclusiva para la ciudad de **Arequipa**.
* **Próximo paso en el testeo:** Arrastrar el edificio principal al mapa, registrar los postes de Cayma y realizar un trazado de fibra óptica (`FiberLink`) uniendo la central con una caja de distribución (caja NAP) para auditar sus puertos libres/ocupados.

---

# Guía de Despliegue e Instalación en Linux (Docker)

Para cumplir con el requerimiento de portabilidad absoluta en cualquier distribución Linux (Ubuntu, Debian, Rocky Linux, etc.) y facilitar el consumo web dentro de la empresa, se propone el despliegue mediante contenedores de **Docker**. 

A continuación, se detalla el procedimiento para clonar este entorno e inicializar la plataforma Kuwaiba (Servidor + Base de Datos de Grafos Neo4j + Visor Web).

### 📋 Requisitos Previos en el Servidor Linux
Antes de comenzar, el servidor debe tener instalado Docker y su complemento de composición. En cualquier distribución Linux (ej. Ubuntu Server), se ejecuta:
```bash
sudo apt update && sudo apt install -y docker.io docker-compose-plugin
sudo systemctl enable --now docker
