# Laboratorio 5: Análisis de Protocolo SSH y HASSH

## Descripción

Este repositorio contiene los archivos de configuración `Dockerfile` desarrollados para la evaluación del Laboratorio 5. El objetivo principal del laboratorio es analizar la evolución criptográfica del protocolo OpenSSH a través de la captura de tráfico y extracción de firmas HASSH.

## Estructura del Repositorio


El repositorio está organizado de la siguiente manera:
    
   -   `Dockerfile_C1`: Configuración para el Cliente 1 (Ubuntu 16.10 - OpenSSH 7.3p1).
       
   -   `Dockerfile_C2`: Configuración para el Cliente 2 (Ubuntu 18.10 - OpenSSH 7.7p1).
       
   -   `Dockerfile_C3`: Configuración para el Cliente 3 (Ubuntu 20.10 - OpenSSH 8.3p1).
       
   -   `Dockerfile_C4S1`: Configuración para el Cliente 4 y Servidor S1 (Ubuntu 22.10 - OpenSSH 9.0p1). _Incluye la creación del usuario "prueba"._
        
-   **`capturas_wireshark/`** (Evidencia forense en formato `.pcap` para Wireshark):
    
    -   `captura_c1.pcap`: Handshake del Cliente 1 al Servidor.
        
    -   `captura_c2.pcap`: Handshake del Cliente 2 al Servidor.
        
    -   `captura_c3.pcap`: Handshake del Cliente 3 al Servidor.
        
    -   `captura_c4.pcap`: Handshake interno de C4 hacia S1 (interfaz `lo`).
        
    -   `captura_informante.pcap`: Tráfico replicado del informante con versión ocultada (`OpenSSH_?`) forzando la interfaz `eth0`.
        
    -   `captura_parte3.pcap`: Captura del servidor modificado con tamaño de _Key Exchange Init_ menor a 300 bytes.
        

## Instrucciones de Uso

Para compilar y levantar cualquiera de los contenedores localmente, ejecute los siguientes comandos en su terminal (ejemplo con C1):

**1. Compilar la imagen:**

```
docker build -t cliente1 -f Dockerfile-C1 .

```

**2. Ejecutar el contenedor (Modo interactivo para clientes):**

```
docker run -it --name c1 cliente1

```

**3. Ejecutar el servidor:**

```
docker build -t servidor1 -f Dockerfile-C4-S1 .
docker run -d --name s1 servidor1
