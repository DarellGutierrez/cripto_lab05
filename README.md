# Laboratorio 5: Análisis de Protocolo SSH y HASSH

## Descripción

Este repositorio contiene los archivos de configuración `Dockerfile` desarrollados para la evaluación del Laboratorio 5. El objetivo principal del laboratorio es analizar la evolución criptográfica del protocolo OpenSSH a través de la captura de tráfico y extracción de firmas HASSH.

## Estructura del Repositorio

El repositorio cuenta con los siguientes archivos:

-   `Dockerfile-C1`: Configuración para el Cliente 1 (Ubuntu 16.10 - OpenSSH 7.3p1).
    
-   `Dockerfile-C2`: Configuración para el Cliente 2 (Ubuntu 18.10 - OpenSSH 7.7p1).
    
-   `Dockerfile-C3`: Configuración para el Cliente 3 (Ubuntu 20.10 - OpenSSH 8.3p1).
    
-   `Dockerfile-C4-S1`: Configuración para el Cliente 4 y Servidor S1 (Ubuntu 22.10 - OpenSSH 9.0p1). _Incluye la creación del usuario "prueba"._

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
