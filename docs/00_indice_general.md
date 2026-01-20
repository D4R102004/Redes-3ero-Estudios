# 📚 Índice General del Curso - Redes de Computadoras

> **Mapa completo del curso con seguimiento de progreso**

**Fecha de inicio:** ___/___/______  
**Objetivo:** Completar en 3 días intensivos  
**Última actualización:** 19 Enero 2026

---

## 🎯 Objetivo del Curso

Aprender Redes de Computadoras desde cero absoluto hasta un nivel profesional, con enfoque 100% práctico y preparación para exámenes universitarios.

---

## 📊 Progreso General

```
████░░░░░░░░░░░░░░░░  10% - Infraestructura completada
```

| Módulo | Estado | Progreso | Horas invertidas |
|--------|--------|----------|------------------|
| **Setup** | ✅ Completado | 100% | __ h |
| **Módulo 00** | ⏳ Pendiente | 0% | __ h |
| **Módulo 01** | ⏳ Pendiente | 0% | __ h |
| **Módulo 02** | ⏳ Pendiente | 0% | __ h |
| **Módulo 03** | ⏳ Pendiente | 0% | __ h |
| **Módulo 04** | ⏳ Pendiente | 0% | __ h |
| **Módulo 05** | ⏳ Pendiente | 0% | __ h |
| **Módulo 06** | ⏳ Pendiente | 0% | __ h |

**Leyenda:**
- ✅ Completado
- 🔄 En progreso
- ⏳ Pendiente
- ⏸️  En pausa
- ❌ Bloqueado

---

## 📅 Plan de Estudio (3 Días)

### Día 1: Fundamentos e Infraestructura (8-10h)

#### Sesión Mañana (4-5h)
- [x] ✅ **Setup del proyecto** (Issue #1) - 2-3h
  - [x] Estructura de carpetas
  - [x] Configuración de herramientas
  - [x] Pre-commit hooks
- [ ] ⏳ **MkDocs** (Issue #2) - 1h
  - [ ] Configurar MkDocs Material
  - [ ] Crear estructura inicial de docs

#### Sesión Tarde (4-5h)
- [ ] ⏳ **Módulo 00: Fundamentos** (Issue #3) - 3-4h
  - [ ] ¿Qué es una red?
  - [ ] Comunicación básica
  - [ ] Casos de uso
  - [ ] Primer código: simulación simple

---

### Día 2: Capas Inferiores (10-12h)

#### Sesión Mañana (5-6h)
- [ ] ⏳ **Módulo 01: Capa Física** (Issue #4)
  - [ ] Señales y modulación
  - [ ] Medios de transmisión
  - [ ] Multiplexación
  - [ ] Código: simulador de señales

#### Sesión Tarde (5-6h)
- [ ] ⏳ **Módulo 02: Capa de Enlace** (Issue #5)
  - [ ] Tramas Ethernet
  - [ ] Direcciones MAC
  - [ ] Switches
  - [ ] Código: simulador de switches

---

### Día 3: Capas Medias y Superiores (10-12h)

#### Sesión Mañana (5-6h)
- [ ] ⏳ **Módulo 03: Capa de Red (IP)** (Issue #6)
  - [ ] Direccionamiento IP
  - [ ] Subnetting
  - [ ] Routing básico
  - [ ] Código: calculadora de subredes

#### Sesión Tarde (5-6h)
- [ ] ⏳ **Módulo 04: Capa de Transporte** (Issue #7)
  - [ ] TCP vs UDP
  - [ ] Puertos
  - [ ] Control de flujo
  - [ ] Código: simulador TCP handshake

---

### Post 3 Días (Opcional)

#### Módulos Avanzados
- [ ] ⏳ **Módulo 05: Enrutamiento** (Issue #8) - 4-5h
  - [ ] RIP, OSPF, BGP
  - [ ] Tablas de enrutamiento
  
- [ ] ⏳ **Módulo 06: Capa de Aplicación** (Issue #9) - 4-5h
  - [ ] HTTP, DNS, FTP
  - [ ] Servicios web

#### Herramientas Extra
- [ ] ⏳ **Módulo 07: Docker** (Issue #10) - 3-4h
- [ ] ⏳ **CI/CD** (Issue #11) - 2-3h

#### Preparación Final
- [ ] ⏳ **Guía de Examen** (Issue #12) - Paralelo
  - [ ] Recopilación de conceptos clave
  - [ ] Exámenes de práctica
  - [ ] Tarjetas de estudio

---

## 🗺️ Estructura Detallada por Módulo

### Módulo 00: Fundamentos de Redes

**Duración:** 3-4 horas | **Dificultad:** ⭐ Básico

#### Objetivos
1. Entender qué es una red sin asumir conocimientos previos
2. Comprender el concepto de comunicación entre dispositivos
3. Identificar casos de uso cotidianos de redes

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/00_fundamentos/README.md`
  - Introducción al módulo
  - Objetivos de aprendizaje
  
- [ ] 📄 `docs/modulos/00_fundamentos/01_que_es_red.md`
  - ¿Qué es una red? (analogía del sistema postal)
  - Elementos básicos: emisor, receptor, mensaje, canal
  - Tipos de redes: LAN, WAN, Internet
  
- [ ] 📄 `docs/modulos/00_fundamentos/02_casos_de_uso.md`
  - WhatsApp / Email
  - Streaming (Netflix, Spotify)
  - Videojuegos online
  - Transferencia de archivos
  - Navegación web

##### Código
- [ ] 💻 `src/redes/ejemplos/modulo00_comunicacion_simple.py`
  - Simulación visual de comunicación
  - Usa biblioteca `rich` para output bonito
  - Muestra envío de mensaje paso a paso

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo00_ejercicio01.py`
  - Implementar función de envío simple
  - Con validaciones básicas

##### Tests
- [ ] ✅ `tests/test_ejemplos/test_modulo00.py`
  - Tests de los ejemplos
  
- [ ] ✅ `tests/test_ejercicios/test_modulo00.py`
  - Tests de ejercicios

##### Autoevaluación
- [ ] 📝 `docs/modulos/00_fundamentos/autoevaluacion.md`
  - 10 preguntas de repaso
  - Respuestas al final

---

### Módulo 01: Capa Física

**Duración:** 4-5 horas | **Dificultad:** ⭐⭐ Intermedio

#### Objetivos
1. Entender cómo se transmite información físicamente
2. Comprender señales analógicas vs digitales
3. Conocer diferentes medios de transmisión

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/01_capa_fisica/README.md`
- [ ] 📄 `docs/modulos/01_capa_fisica/01_senales.md`
  - Señales analógicas y digitales
  - Modulación (AM, FM, PM)
  - Ancho de banda
  
- [ ] 📄 `docs/modulos/01_capa_fisica/02_medios.md`
  - Cable de cobre (par trenzado, coaxial)
  - Fibra óptica
  - Inalámbrico (Wi-Fi, celular)
  
- [ ] 📄 `docs/modulos/01_capa_fisica/03_multiplexacion.md`
  - TDM (Time Division Multiplexing)
  - FDM (Frequency Division Multiplexing)

##### Código
- [ ] 💻 `src/redes/ejemplos/modulo01_senales.py`
  - Visualización de señales con matplotlib
  
- [ ] 💻 `src/redes/ejemplos/modulo01_modulacion.py`
  - Simulación de modulación AM/FM

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo01_ejercicio01.py`
  - Calcular ancho de banda
- [ ] 📝 `src/redes/ejercicios/modulo01_ejercicio02.py`
  - Simular multiplexación TDM

##### Tests
- [ ] ✅ `tests/test_ejemplos/test_modulo01.py`
- [ ] ✅ `tests/test_ejercicios/test_modulo01.py`

##### Autoevaluación
- [ ] 📝 `docs/modulos/01_capa_fisica/autoevaluacion.md`

---

### Módulo 02: Capa de Enlace

**Duración:** 4-5 horas | **Dificultad:** ⭐⭐ Intermedio

#### Objetivos
1. Entender cómo se organizan los bits en tramas
2. Comprender direcciones MAC
3. Conocer funcionamiento de switches

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/02_capa_enlace/README.md`
- [ ] 📄 `docs/modulos/02_capa_enlace/01_tramas.md`
  - Estructura de trama Ethernet
  - Campos: preámbulo, direcciones, datos, FCS
  
- [ ] 📄 `docs/modulos/02_capa_enlace/02_mac.md`
  - ¿Qué es una dirección MAC?
  - Formato: `AA:BB:CC:DD:EE:FF`
  - Unicast, Multicast, Broadcast
  
- [ ] 📄 `docs/modulos/02_capa_enlace/03_switches.md`
  - Funcionamiento de switches
  - Tabla CAM
  - VLAN básico

##### Código
- [ ] 💻 `src/redes/ejemplos/modulo02_trama.py`
  - Crear y parsear tramas Ethernet
  
- [ ] 💻 `src/redes/simuladores/switch_simulator.py`
  - Simulador interactivo de switch

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo02_ejercicio01.py`
  - Validar direcciones MAC
- [ ] 📝 `src/redes/ejercicios/modulo02_ejercicio02.py`
  - Calcular FCS (checksum)

##### Tests
- [ ] ✅ `tests/test_ejemplos/test_modulo02.py`
- [ ] ✅ `tests/test_ejercicios/test_modulo02.py`

---

### Módulo 03: Capa de Red (IP)

**Duración:** 5-6 horas | **Dificultad:** ⭐⭐⭐ Avanzado

#### Objetivos
1. Dominar direccionamiento IPv4
2. Entender y practicar subnetting
3. Comprender routing básico

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/03_capa_red/README.md`
- [ ] 📄 `docs/modulos/03_capa_red/01_ipv4.md`
  - Estructura de dirección IP
  - Clases (A, B, C, D, E)
  - Direcciones especiales
  
- [ ] 📄 `docs/modulos/03_capa_red/02_subnetting.md`
  - Máscaras de subred
  - Cálculo de red, broadcast, hosts
  - CIDR notation
  
- [ ] 📄 `docs/modulos/03_capa_red/03_routing.md`
  - Tablas de routing
  - Routing estático vs dinámico
  - Algoritmo básico

##### Código
- [ ] 💻 `src/redes/ejemplos/modulo03_ip.py`
  - Clase IP con operaciones
  
- [ ] 💻 `src/redes/utils/subnet_calculator.py`
  - Calculadora de subnetting completa

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo03_subnetting.py`
  - 10 ejercicios de subnetting progresivos

##### Tests
- [ ] ✅ `tests/test_ejemplos/test_modulo03.py`
- [ ] ✅ `tests/test_ejercicios/test_modulo03.py`

---

### Módulo 04: Capa de Transporte

**Duración:** 4-5 horas | **Dificultad:** ⭐⭐⭐ Avanzado

#### Objetivos
1. Entender diferencias TCP vs UDP
2. Comprender puertos y sockets
3. Conocer control de flujo y congestión

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/04_capa_transporte/README.md`
- [ ] 📄 `docs/modulos/04_capa_transporte/01_tcp_udp.md`
  - Características de TCP
  - Características de UDP
  - Cuándo usar cada uno
  
- [ ] 📄 `docs/modulos/04_capa_transporte/02_puertos.md`
  - ¿Qué es un puerto?
  - Puertos conocidos (0-1023)
  - Puertos efímeros
  
- [ ] 📄 `docs/modulos/04_capa_transporte/03_control.md`
  - Three-way handshake
  - Sliding window
  - Control de congestión

##### Código
- [ ] 💻 `src/redes/simuladores/tcp_handshake.py`
  - Visualización del handshake
  
- [ ] 💻 `src/redes/ejemplos/modulo04_sockets.py`
  - Cliente y servidor básicos

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo04_chat_simple.py`
  - Implementar chat TCP básico

##### Tests
- [ ] ✅ `tests/test_ejemplos/test_modulo04.py`
- [ ] ✅ `tests/test_simuladores/test_tcp.py`

---

### Módulo 05: Enrutamiento

**Duración:** 4-5 horas | **Dificultad:** ⭐⭐⭐⭐ Muy Avanzado

#### Objetivos
1. Entender protocolos de enrutamiento
2. Comprender RIP, OSPF, BGP conceptualmente
3. Analizar tablas de enrutamiento

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/05_enrutamiento/README.md`
- [ ] 📄 `docs/modulos/05_enrutamiento/01_protocolos.md`
  - Vector distancia vs Estado de enlace
  - Métricas (hop count, bandwidth, etc.)
  
- [ ] 📄 `docs/modulos/05_enrutamiento/02_rip_ospf.md`
  - RIP: Funcionamiento, ventajas, desventajas
  - OSPF: Areas, LSA, SPF
  
- [ ] 📄 `docs/modulos/05_enrutamiento/03_bgp.md`
  - Enrutamiento entre AS
  - Políticas de routing

##### Código
- [ ] 💻 `src/redes/simuladores/routing_simulator.py`
  - Simulador de RIP

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo05_tablas.py`
  - Interpretar y construir tablas de routing

##### Tests
- [ ] ✅ `tests/test_simuladores/test_routing.py`

---

### Módulo 06: Capa de Aplicación

**Duración:** 4-5 horas | **Dificultad:** ⭐⭐ Intermedio

#### Objetivos
1. Entender protocolos de aplicación comunes
2. Implementar cliente HTTP simple
3. Comprender DNS

#### Contenido

##### Teoría
- [ ] 📄 `docs/modulos/06_capa_aplicacion/README.md`
- [ ] 📄 `docs/modulos/06_capa_aplicacion/01_http.md`
  - Métodos (GET, POST, etc.)
  - Headers
  - Códigos de estado
  
- [ ] 📄 `docs/modulos/06_capa_aplicacion/02_dns.md`
  - Resolución de nombres
  - Tipos de registros
  - Jerarquía DNS
  
- [ ] 📄 `docs/modulos/06_capa_aplicacion/03_otros.md`
  - FTP, SMTP, SSH

##### Código
- [ ] 💻 `src/redes/ejemplos/modulo06_http_client.py`
  - Cliente HTTP simple
  
- [ ] 💻 `src/redes/ejemplos/modulo06_dns_query.py`
  - Consultas DNS

##### Ejercicios
- [ ] 📝 `src/redes/ejercicios/modulo06_web_scraper.py`
  - Scraper simple usando sockets

##### Tests
- [ ] ✅ `tests/test_ejemplos/test_modulo06.py`

---

## 🔗 Referencias Cruzadas

### Dependencias entre Módulos

```
Módulo 00 (Fundamentos)
    ↓ requiere
Módulo 01 (Física) ─────→ Módulo 02 (Enlace)
                              ↓ requiere
                          Módulo 03 (Red/IP)
                              ↓ requiere
                          Módulo 04 (Transporte)
                              ↓ requiere
                          Módulo 05 (Enrutamiento)
                              ↓ usa
                          Módulo 06 (Aplicación)
```

### Conceptos Clave por Módulo

| Concepto | Módulos que lo usan |
|----------|---------------------|
| Direcciones | 02 (MAC), 03 (IP) |
| Protocolos | 02 (Ethernet), 03 (IP), 04 (TCP/UDP), 05 (RIP/OSPF), 06 (HTTP/DNS) |
| Encapsulación | 01, 02, 03, 04, 06 |
| Routing | 03, 05 |
| Puertos | 04, 06 |

---

## 📖 Material de Apoyo

### PDFs Disponibles
- [ ] `materiales/conferencias/Conf_1_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_2_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_3_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_4_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_5_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_6_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_7_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_9_Redes__2025.pdf`
- [ ] `materiales/conferencias/Conf_10_Redes__2025.pdf`

### Herramientas de Red
- [ ] Wireshark instalado
- [ ] GNS3 (opcional)
- [ ] Packet Tracer (opcional)

---

## ✅ Checklist Final

### Antes del Examen
- [ ] Completados al menos 5 de 7 módulos principales
- [ ] Todos los ejercicios resueltos y testeados
- [ ] Al menos 2 simulaciones ejecutadas
- [ ] Autoevaluaciones completadas (score >80%)
- [ ] Repasadas todas las analogías clave
- [ ] Practicados ejercicios de exámenes anteriores

---

## 📝 Notas de Progreso

### Día 1 - ___/___/______
**Horas:** ____  
**Completado:**
- 

**Aprendizajes clave:**
- 

**Dudas pendientes:**
- 

---

### Día 2 - ___/___/______
**Horas:** ____  
**Completado:**
- 

**Aprendizajes clave:**
- 

**Dudas pendientes:**
- 

---

### Día 3 - ___/___/______
**Horas:** ____  
**Completado:**
- 

**Aprendizajes clave:**
- 

**Dudas pendientes:**
- 

---

## 🎯 Métricas de Éxito

### Conocimiento Teórico
- [ ] Puedo explicar qué es una red a alguien que no sabe nada
- [ ] Entiendo las 7 capas del modelo OSI
- [ ] Puedo hacer subnetting mentalmente
- [ ] Conozco las diferencias TCP vs UDP
- [ ] Entiendo cómo funciona routing

### Habilidades Prácticas
- [ ] He ejecutado al menos 10 ejemplos de código
- [ ] He completado al menos 15 ejercicios
- [ ] He usado Wireshark al menos 3 veces
- [ ] Puedo crear un cliente/servidor básico
- [ ] Puedo analizar una captura de paquetes

### Preparación para Examen
- [ ] Score >80% en todas las autoevaluaciones
- [ ] Completado al menos 1 examen de práctica completo
- [ ] Revisadas todas las conferencias del profesor
- [ ] Creadas tarjetas de estudio (flashcards)

---

**Última actualización:** 19 Enero 2026  
**Próximo paso:** Comenzar con Módulo 00

