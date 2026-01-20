# 🚨 ISSUES ADICIONALES CRÍTICOS - Para Cubrir Examen Completo

**Fecha:** 19 Enero 2026
**Urgencia:** ALTA
**Razón:** Estos issues cubren contenido que APARECE en exámenes pero no está suficientemente cubierto en los issues 1-12

---

## 📊 Análisis de Vacíos

Después de revisar el **Examen Extraordinario 2017-2018** identifico estos vacíos críticos:

### Pregunta 1 del examen (35 puntos): Subnetting complejo
- **Requiere:** Cálculos rápidos y precisos de subredes
- **Estado actual:** Issue #6 cubre teoría pero FALTA práctica intensiva

### Pregunta 2 del examen (10 puntos): Rastreo completo de paquetes
- **Requiere:** Seguir cada trama con MACs, IPs, puertos, protocolos
- **Estado actual:** NO cubierto específicamente

### Pregunta 4 del examen (50 puntos): V/F con justificación
- **Requiere:** Conocimiento profundo de detalles técnicos
- **Estado actual:** Autoevaluaciones existen pero NO suficientes

### Conceptos NO suficientemente cubiertos:
- Dispositivos de red (Hub, Switch, Router) a nivel de capas
- Dominios de colisión
- CRC implementado
- Detalles de protocolos (flags, campos específicos)

---

# Issue #13: Crear Módulo 08 - Dispositivos de Red y Dominios de Colisión

**Labels:** `enhancement`, `documentation`, `modulo`, `dispositivos`, `prioridad-CRÍTICA`
**Dependencias:** Issue #5 (Capa de Enlace)

## Descripción

Crear módulo específico que explica los diferentes dispositivos de red (Hub/Repetidor, Switch, Router) y conceptos fundamentales como **dominios de colisión** y **dominios de broadcast**. Este contenido aparece frecuentemente en exámenes pero no está suficientemente cubierto en otros módulos.

**CRÍTICO:** El examen pregunta específicamente sobre:
- "Un repetidor(Hub) define un dominio de colisión"
- "Un router procesa hasta la capa de transporte" (F - solo hasta Red)
- "Switches siempre envían cada paquete por todos los puertos" (F)
- "Las tablas de rutas asocian direcciones IP con direcciones MAC" (F)

## Objetivos

1. Explicar cada dispositivo de red y hasta qué capa OSI/TCP-IP procesa
2. Introducir concepto de **dominio de colisión** de forma clara
3. Explicar diferencia entre **Hub** (capa 1) vs **Switch** (capa 2) vs **Router** (capa 3)
4. Mostrar cómo funcionan las **tablas MAC** en switches
5. Explicar **Ethernet** y el problema de colisiones (CSMA/CD)
6. Implementar simulador visual de colisiones

## Tareas

1. **Crear archivo principal de teoría:**
   - Crear `docs/modulos/08_dispositivos/README.md`
   - Sección "Dispositivos de red por capa":
     - **Capa 1 (Física): Hub/Repetidor**
       - Qué hace: Repite señal eléctrica por todos los puertos
       - NO mira contenido del paquete
       - Todos los dispositivos conectados = **1 dominio de colisión**
       - Requiere CSMA/CD (Carrier Sense Multiple Access with Collision Detection)
       - Analogía: Megáfono que amplifica todo lo que escucha
     - **Capa 2 (Enlace): Switch/Puente**
       - Qué hace: Lee dirección MAC y reenvía solo por puerto correcto
       - Mantiene **tabla MAC** (MAC → puerto)
       - Aprende MACs observando tráfico
       - Separa dominios de colisión (cada puerto = dominio independiente)
       - Si MAC no está en tabla → broadcast por todos los puertos
       - Analogía: Cartero que lee direcciones y entrega específicamente
     - **Capa 3 (Red): Router**
       - Qué hace: Lee dirección IP y toma decisiones de enrutamiento
       - Mantiene **tabla de enrutamiento** (red → interfaz/next hop)
       - NO asocia IP con MAC (eso es tabla ARP, diferente)
       - Separa dominios de broadcast
       - Analogía: Director de tráfico que decide rutas

2. **Explicar dominios de colisión:**
   - Crear `docs/modulos/08_dispositivos/01_dominios_colision.md`
   - **¿Qué es una colisión?**
     - Cuando dos dispositivos transmiten simultáneamente en mismo medio compartido
     - Las señales se mezclan → datos corruptos
     - Solo ocurre en medios compartidos (half-duplex)
   - **Dominio de colisión:**
     - Conjunto de dispositivos que comparten el mismo medio y pueden colisionar
     - Hub: Todos los puertos = 1 dominio
     - Switch: Cada puerto = dominio separado (no hay colisiones)
   - **CSMA/CD** (Carrier Sense Multiple Access with Collision Detection):
     - Escuchar antes de transmitir
     - Si detecta colisión → parar y esperar tiempo aleatorio
     - Reintentar
   - **¿Colisión = mal funcionamiento?**
     - NO necesariamente
     - En redes con Hub es NORMAL tener algunas colisiones
     - Solo es problema si hay MUCHAS (>10% del tráfico)

3. **Explicar tabla MAC del switch:**
   - Crear `docs/modulos/08_dispositivos/02_tabla_mac.md`
   - Cómo funciona:
     ```
     Switch recibe frame por puerto 1
     → Lee MAC origen → Aprende "MAC-A está en puerto 1"
     → Lee MAC destino
     → Si MAC destino en tabla → Envía solo por ese puerto
     → Si MAC destino NO en tabla → Broadcast por todos (excepto origen)
     ```
   - Tabla MAC ejemplo:
     ```
     MAC Address        | Puerto | Tiempo
     AA:BB:CC:DD:EE:01 | 1      | 60s
     AA:BB:CC:DD:EE:02 | 2      | 45s
     AA:BB:CC:DD:EE:03 | 1      | 30s
     ```
   - TTL de entradas (timeout, usualmente 300s)

4. **Explicar Ethernet y CSMA/CD:**
   - Crear `docs/modulos/08_dispositivos/03_ethernet.md`
   - Ethernet es un PROTOCOLO de capa de enlace
   - Define:
     - Formato de frame
     - Direccionamiento (MAC)
     - Método de acceso al medio (CSMA/CD)
   - CSMA/CD paso a paso:
     1. Quiero enviar → Escucho medio
     2. ¿Ocupado? → Espero
     3. ¿Libre? → Transmito
     4. Mientras transmito → Sigo escuchando
     5. ¿Detecto colisión? → Paro, envío señal de jam, espero tiempo aleatorio
     6. Reintento (máximo 16 veces)

5. **Crear tabla comparativa de dispositivos:**
   - Crear `docs/modulos/08_dispositivos/04_comparativa.md`
   ```markdown
   | Dispositivo | Capa OSI | Capa TCP/IP | Función | Dominio de colisión | Lee |
   |-------------|----------|-------------|---------|---------------------|-----|
   | Hub/Repetidor | 1 (Física) | - | Amplifica señal | 1 solo | Nada (solo señal) |
   | Switch/Puente | 2 (Enlace) | Link | Reenvía por MAC | Múltiples (1 por puerto) | MAC |
   | Router | 3 (Red) | Internet | Enruta por IP | Múltiples | IP (NO procesa hasta Transporte) |
   ```

6. **Crear ejemplos de código - Simulador de colisiones:**
   - Crear `src/redes/ejemplos/08_dispositivos/simulador_colisiones.py`
   - Simular red con Hub:
     ```python
     class Hub:
         """Simula Hub que causa colisiones."""
         def __init__(self, num_puertos: int):
             self.puertos = num_puertos
             self.dispositivos = []

         def conectar_dispositivo(self, dispositivo):
             """Conecta dispositivo al hub."""

         def transmitir(self, origen, datos):
             """
             Transmite por TODOS los puertos.
             Si múltiples dispositivos transmiten simultáneamente → colisión.
             """
             # Simular broadcast
             # Detectar colisiones si >1 transmitiendo

         def visualizar_colision(self):
             """Muestra visualmente colisión con rich."""
     ```

7. **Crear simulador de Switch:**
   - Crear `src/redes/ejemplos/08_dispositivos/simulador_switch.py`
   - Implementar tabla MAC con aprendizaje:
     ```python
     class Switch:
         """Simula switch con tabla MAC."""
         def __init__(self):
             self.tabla_mac: dict[str, int] = {}  # MAC → puerto
             self.ttl: dict[str, int] = {}  # MAC → tiempo restante

         def recibir_frame(self, puerto_origen: int, mac_origen: str, mac_destino: str, datos: str):
             """Procesa frame y actualiza tabla."""
             # Aprender MAC origen
             self.tabla_mac[mac_origen] = puerto_origen
             self.ttl[mac_origen] = 300  # 5 minutos

             # Buscar MAC destino
             if mac_destino in self.tabla_mac:
                 puerto_destino = self.tabla_mac[mac_destino]
                 # Enviar solo por ese puerto
             else:
                 # Broadcast por todos excepto origen

         def mostrar_tabla(self):
             """Muestra tabla MAC con rich."""
     ```

8. **Crear ejercicios tipo examen:**
   - Crear `docs/modulos/08_dispositivos/05_ejercicios_examen.md`
   - **Verdadero/Falso** (con justificación):
     - [ ] "Un repetidor(Hub) define un dominio de colisión"
       - **Respuesta:** VERDADERO
       - **Justificación:** El hub repite señal por todos los puertos, creando un medio compartido donde todos pueden colisionar entre sí.

     - [ ] "La ocurrencia de colisiones en una red Ethernet es síntoma seguro de mal funcionamiento"
       - **Respuesta:** FALSO
       - **Justificación:** En redes con hubs, algunas colisiones son normales (parte de CSMA/CD). Solo es problema si son excesivas.

     - [ ] "Un router procesa hasta la capa de transporte del modelo TCP/IP"
       - **Respuesta:** FALSO
       - **Justificación:** El router procesa hasta la capa de RED (capa 3). NO lee puertos (capa 4).

     - [ ] "Los switches siempre envían cada paquete por todos los puertos"
       - **Respuesta:** FALSO
       - **Justificación:** Solo hacen broadcast si la MAC destino NO está en su tabla. Normalmente envían solo por el puerto correspondiente.

     - [ ] "Las tablas de rutas asocian direcciones IP con direcciones MAC"
       - **Respuesta:** FALSO
       - **Justificación:** Las tablas de RUTAS asocian redes IP con interfaces/next hops. La asociación IP↔MAC es de las tablas ARP.

     - [ ] "En una red, todos los routers y switches tienen asignadas una o varias direcciones IP"
       - **Respuesta:** FALSO
       - **Justificación:** Los switches (capa 2) NO requieren IP para funcionar. Solo los routers (capa 3) necesitan IPs.

   - **[30+ preguntas más tipo examen]**

9. **Crear autoevaluación:**
   - Al final de README.md
   - 20 preguntas enfocadas en dispositivos y dominios de colisión

10. **Actualizar Issue #5 (Capa de Enlace):**
    - Añadir link a Módulo 08 para profundizar en dispositivos
    - Cross-reference

## Criterios de aceptación

- [ ] Módulo 08 explica Hub, Switch, Router a nivel de capas
- [ ] Concepto de dominio de colisión está claro con analogías
- [ ] CSMA/CD explicado paso a paso
- [ ] Tabla comparativa de dispositivos completa
- [ ] Simulador de colisiones funciona y visualiza con rich
- [ ] Simulador de switch implementa tabla MAC con aprendizaje
- [ ] Al menos 30 preguntas V/F tipo examen con justificaciones
- [ ] Un estudiante puede explicar por qué "router procesa hasta capa 3"
- [ ] Un estudiante puede explicar cuándo un switch hace broadcast

---

# Issue #14: Crear Banco Masivo de Ejercicios de Subnetting

**Labels:** `enhancement`, `ejercicios`, `subnetting`, `prioridad-CRÍTICA`
**Dependencias:** Issue #6 (Módulo 03 - Capa de Red)

## Descripción

Crear banco de **100+ ejercicios** de subnetting con dificultad progresiva. La pregunta 1 del examen (35 puntos - más de 1/3 del total) es PURO cálculo de subredes. Necesitas poder hacer estos cálculos **rápido y sin errores**.

**CRÍTICO:** En el examen debes:
- Asignar subredes a topología compleja
- Calcular rango de direcciones
- Calcular broadcast
- Determinar máscara más ajustada para N equipos
- Completar tabla de enrutamiento

TODO esto bajo presión de tiempo.

## Objetivos

1. Practicar cálculos de subredes hasta hacerlo automático
2. Dominar notación CIDR
3. Calcular subredes de forma visual (sin calculadora)
4. Poder hacerlo en <2 minutos por ejercicio
5. Reducir errores a 0%

## Tareas

1. **Crear generador automático de ejercicios:**
   - Crear `src/redes/ejercicios/generador_subnetting.py`
   - Genera ejercicios aleatorios:
     ```python
     class GeneradorSubnetting:
         """Genera ejercicios de subnetting aleatorios."""

         def generar_ejercicio_basico(self) -> dict:
             """
             Ejercicio: Dada IP/máscara, calcular red, broadcast, rango.
             """
             # Generar IP y máscara aleatorias
             # Calcular respuestas correctas
             return {
                 "pregunta": "Dada IP 192.168.50.130/26...",
                 "respuestas": {...}
             }

         def generar_ejercicio_division(self) -> dict:
             """
             Ejercicio: Dividir red en N subredes.
             """

         def generar_ejercicio_topologia(self) -> dict:
             """
             Ejercicio: Asignar subredes a topología (como examen).
             """
     ```

2. **Crear categorías de ejercicios:**

   **Nivel 1: Básico (20 ejercicios)**
   - Crear `docs/examenes/ejercicios/subnetting_nivel1.md`
   - Dados IP/máscara, calcular:
     - Dirección de red
     - Broadcast
     - Rango de hosts
     - Cantidad de hosts
   - Ejemplo:
     ```
     IP: 192.168.1.100/24
     Red: _____________
     Broadcast: _____________
     Rango: desde _______ hasta _______
     Hosts: _______
     ```

   **Nivel 2: Intermedio (30 ejercicios)**
   - Crear `docs/examenes/ejercicios/subnetting_nivel2.md`
   - Dividir red en subredes:
     ```
     Red: 172.16.0.0/16
     Dividir en 4 subredes iguales

     Subred 1: _____________/___
     Subred 2: _____________/___
     Subred 3: _____________/___
     Subred 4: _____________/___
     ```

   **Nivel 3: Avanzado (30 ejercicios)**
   - Crear `docs/examenes/ejercicios/subnetting_nivel3.md`
   - VLSM (Variable Length Subnet Mask):
     ```
     Red: 10.0.0.0/8
     Necesitas subredes para:
     - 500 hosts
     - 200 hosts
     - 50 hosts
     - 10 hosts

     Asigna la máscara más eficiente para cada una
     ```

   **Nivel 4: Tipo Examen (20 ejercicios)**
   - Crear `docs/examenes/ejercicios/subnetting_nivel4.md`
   - Topologías completas como el examen
   - Completar tabla de enrutamiento
   - Calcular máscara para X equipos

3. **Crear herramienta de práctica interactiva:**
   - Crear `src/redes/ejercicios/practica_subnetting.py`
   - CLI con typer:
     ```python
     import typer

     app = typer.Typer()

     @app.command()
     def practicar(nivel: int = 1, cantidad: int = 10):
         """Genera ejercicios y verifica respuestas."""
         # Generar ejercicio
         # Usuario ingresa respuestas
         # Verificar
         # Mostrar estadísticas (aciertos/fallos)

     @app.command()
     def cronometrado():
         """Modo examen: 10 ejercicios en 20 minutos."""
         # Cronómetro
         # Puntaje final
     ```

4. **Crear métodos de cálculo rápido:**
   - Crear `docs/examenes/recursos/calculos_rapidos_subredes.md`
   - Trucos y atajos:
     ```markdown
     ## Método rápido para calcular hosts

     Máscara /24 → 32-24 = 8 bits de host
     Hosts = 2^8 - 2 = 256 - 2 = 254

     Máscara /26 → 32-26 = 6 bits
     Hosts = 2^6 - 2 = 64 - 2 = 62

     ## Tabla de referencia rápida

     | CIDR | Máscara | Hosts |
     |------|---------|-------|
     | /30 | 255.255.255.252 | 2 |
     | /29 | 255.255.255.248 | 6 |
     | /28 | 255.255.255.240 | 14 |
     | /27 | 255.255.255.224 | 30 |
     | /26 | 255.255.255.192 | 62 |
     | /25 | 255.255.255.128 | 126 |
     | /24 | 255.255.255.0 | 254 |
     | /16 | 255.255.0.0 | 65534 |
     | /8 | 255.0.0.0 | 16777214 |

     ## Método visual para broadcast

     IP: 192.168.1.100/26
     Máscara: 255.255.255.192

     Último octeto:
     100 en binario: 01100100
     Máscara 192: 11000000

     Bits de host (0s en máscara) = 6
     Ponerlos todos en 1:
     01111111 = 127

     → Broadcast parte de red + bits de host en 1
     192.168.1.127
     ```

5. **Crear soluciones paso a paso:**
   - Para cada ejercicio, solución detallada
   - Mostrar proceso de pensamiento
   - Explicar errores comunes

6. **Crear tracker de progreso:**
   - Archivo `docs/examenes/progreso_subnetting.md`
   - Checklist de ejercicios completados
   - Estadísticas: % aciertos, tiempo promedio

## Criterios de aceptación

- [ ] Existen 100+ ejercicios de subnetting únicos
- [ ] Ejercicios organizados en 4 niveles de dificultad
- [ ] Generador automático funciona y crea ejercicios aleatorios
- [ ] Herramienta de práctica interactiva funciona con cronómetro
- [ ] Guía de cálculos rápidos con trucos y tablas de referencia
- [ ] Todas las soluciones incluyen explicación paso a paso
- [ ] Tracker de progreso permite ver estadísticas
- [ ] Un estudiante puede resolver ejercicio básico en <2 min
- [ ] Un estudiante puede resolver ejercicio avanzado en <5 min

---

# Issue #15: Crear Banco de 200+ Preguntas Verdadero/Falso Tipo Examen

**Labels:** `enhancement`, `examenes`, `verdadero-falso`, `prioridad-CRÍTICA`
**Dependencias:** Issues #3-9 (todos los módulos)

## Descripción

Crear banco masivo de preguntas Verdadero/Falso con justificaciones detalladas. La pregunta 4 del examen vale **50 puntos** (la mitad del examen total) y consiste SOLO en V/F. Necesitas dominar los detalles técnicos de TODOS los temas.

**CRÍTICO:** Estas preguntas tienen "trampas":
- "El modelo TCP/IP define 7 capas" (F - define 4, OSI define 7)
- "UDP utiliza flag ACK" (F - UDP no tiene flags)
- "Three-way handshake es para UDP" (F - es para TCP)

Debes saber identificar y justificar cada una.

## Objetivos

1. Tener 200+ preguntas V/F cubriendo TODO el temario
2. Cada pregunta con justificación detallada
3. Identificar "palabras trampa" típicas
4. Practicar justificaciones como en examen real
5. Dominar detalles técnicos finos

## Tareas

1. **Organizar preguntas por módulo:**

   **Módulo 00: Fundamentos (15 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo00.md`

   **Módulo 01: Capa Física (20 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo01.md`
   - Ejemplos:
     - [ ] "La fibra óptica transmite electricidad" (F)
     - [ ] "El cable Cat6 es más rápido que Cat5e" (V)
     - [ ] "WiFi es inmune a interferencias" (F)

   **Módulo 02: Capa de Enlace (25 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo02.md`
   - Ejemplos:
     - [ ] "El checksum puede corregir errores" (F - solo detecta)
     - [ ] "Stop-and-Wait es más rápido que Sliding Window" (F)
     - [ ] "CRC detecta todos los errores posibles" (F - casi todos)

   **Módulo 03: Capa de Red (35 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo03.md`
   - Ejemplos (del examen real):
     - [ ] "Pueden agruparse 200.31.40.16/28 y 200.31.40.32/28 con 200.31.40.16/27" (V)
     - [ ] "El IP 166.233.43.127 es broadcast de 166.233.43.64/26" (V)
     - [ ] "Las tablas de rutas asocian IP con MAC" (F)

   **Módulo 04: Capa de Transporte (30 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo04.md`
   - Ejemplos (del examen real):
     - [ ] "TCP se utiliza para comunicaciones seguras y sin pérdidas" (V - sin pérdidas, pero NO cifradas)
     - [ ] "UDP utiliza flag ACK en su header" (F - UDP no tiene flags)
     - [ ] "Three-way handshake es para UDP" (F - es TCP)
     - [ ] "HTTP utiliza UDP" (F - usa TCP)

   **Módulo 05: Enrutamiento (25 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo05.md`
   - Ejemplos (del examen real):
     - [ ] "En Vector Distancia se intercambia info solo con vecinos" (V)
     - [ ] "En tabla de rutas estáticas solo existen entradas de interfaces propias" (F)
     - [ ] "Si router no encuentra ruta, envía flag al emisor" (F - depende de ICMP)

   **Módulo 06: Capa de Aplicación (30 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo06.md`
   - Ejemplos (del examen real):
     - [ ] "SMTP maneja entrega desde emisor hasta receptor" (V)
     - [ ] "DNS se basa en esquema distribuido jerárquico" (V)
     - [ ] "DNS, HTTP e IMAP están relacionados a email" (F - HTTP no)
     - [ ] "HTTP, SMTP, POP3, IMAP son protocolos de texto plano" (V)
     - [ ] "http://cronos.uh.cu y http://nimbo.uh.cu pueden llegar al mismo IP" (V - mismo servidor)
     - [ ] "DNS usa UDP porque mensajes son pequeños" (V)

   **Módulo 08: Dispositivos (20 preguntas)**
   - Crear `docs/examenes/verdadero_falso/vf_modulo08.md`
   - Ejemplos (del examen real):
     - [ ] "Ocurrencia de colisiones es síntoma de mal funcionamiento" (F)
     - [ ] "Un Hub define un dominio de colisión" (V)
     - [ ] "Un router procesa hasta capa de transporte" (F - solo hasta Red)
     - [ ] "Switches siempre envían por todos los puertos" (F)
     - [ ] "En una red, routers y switches tienen IPs asignadas" (F - switches no necesitan)
     - [ ] "ARP es usado por nodos con capa de enlace para traducir IP→MAC" (V)

2. **Crear formato estándar:**
   ```markdown
   ### Pregunta X

   **Afirmación:** "El protocolo X hace Y"

   **Respuesta:** [ ] Verdadero [ ] Falso

   **Justificación:**
   [Explicación detallada de por qué es V o F]

   **Palabra clave trampa:** [Si aplica]
   [Por ejemplo: "solo", "siempre", "nunca", "todos"]

   **Error común:**
   [Qué confusión típica lleva al error]

   **Referencia:**
   - Módulo: X
   - Sección: Y
   - Conferencia: Z, página W
   ```

3. **Crear herramienta de práctica:**
   - Crear `src/redes/ejercicios/practica_verdadero_falso.py`
   - Modo aleatorio: selecciona 20 preguntas al azar
   - Modo por módulo: selecciona de módulo específico
   - Modo examen: 22 preguntas (como examen real)
   - Cronómetro
   - Estadísticas: % aciertos por módulo

4. **Crear análisis de palabras trampa:**
   - Crear `docs/examenes/recursos/palabras_trampa_vf.md`
   ```markdown
   ## Palabras que indican FALSO:

   - **"siempre"** / **"nunca"** / **"todos"** / **"ninguno"**
     - Rara vez algo es absoluto en redes
     - Ejemplo: "Switches SIEMPRE envían por todos los puertos" → F

   - **"solo"** / **"únicamente"**
     - Ejemplo: "En Vector Distancia SOLO se intercambia con vecinos" → V (esta SÍ es cierta)

   - **"garantiza"** / **"seguro"**
     - Ejemplo: "TCP garantiza comunicación SEGURA" → F (garantiza entrega, NO cifrado)

   ## Palabras que requieren precisión:

   - **"procesa hasta capa X"**
     - Hub: Capa 1
     - Switch: Capa 2
     - Router: Capa 3 (NO procesa puertos/capa 4)

   - **"protocolo de texto plano"**
     - HTTP, SMTP, POP3, IMAP, FTP → V
     - HTTPS → F (está cifrado)
   ```

5. **Crear exámenes de práctica V/F:**
   - 10 exámenes completos de 22 preguntas cada uno
   - Mismo formato que examen real
   - Con cronómetro (tiempo límite)
   - Sistema de calificación

## Criterios de aceptación

- [ ] Existen 200+ preguntas V/F únicas
- [ ] Preguntas organizadas por módulo
- [ ] Cada pregunta tiene justificación detallada
- [ ] Se identifican palabras trampa
- [ ] Herramienta de práctica interactiva funciona
- [ ] 10 exámenes de práctica completos
- [ ] Guía de palabras trampa
- [ ] Un estudiante puede identificar por qué cada afirmación es V o F
- [ ] Un estudiante logra >90% de aciertos después de practicar

---

## 🎯 PRIORIZACIÓN DE ISSUES ACTUALIZADOS

### **Orden de ejecución recomendado:**

**CRÍTICO (hacer primero):**
1. Issue #1: Estructura
2. Issue #2: MkDocs
3. Issue #6: Módulo 03 (Capa de Red - IP y subredes) ← **PRIORIDAD MÁXIMA**
4. **Issue #14: Banco de Subnetting** ← **NUEVO, CRÍTICO**
5. Issue #13: Módulo 08 (Dispositivos) ← **NUEVO, CRÍTICO**

**Alta prioridad:**
6. Issue #3: Módulo 00
7. Issue #5: Módulo 02 (Capa de Enlace)
8. Issue #7: Módulo 04 (TCP/UDP)
9. Issue #9: Módulo 06 (Aplicación)
10. **Issue #15: Banco V/F** ← **NUEVO, CRÍTICO**

**Media prioridad:**
11. Issue #4: Módulo 01
12. Issue #8: Módulo 05
13. Issue #12: Guía de Examen

**Baja prioridad (opcional):**
14. Issue #10: Docker
15. Issue #11: CI/CD

---

## 📊 RESUMEN DE CAMBIOS

**Issues originales:** 12
**Issues nuevos CRÍTICOS:** 3
**Total:** 15 issues

**Nuevos issues:**
- **#13:** Dispositivos de red (Hub/Switch/Router, dominios de colisión)
- **#14:** Banco masivo de subnetting (100+ ejercicios)
- **#15:** Banco de V/F (200+ preguntas)

**Modificaciones a issues existentes:**
- **Issue #6:** Añadir más ejercicios prácticos de subredes
- **Issue #5:** Añadir CRC implementado (no solo teoría)
- **Issue #12:** Integrar bancos de ejercicios de #14 y #15

---

**Estado:** LISTO PARA USAR
**Próximo paso:** Descargar este archivo y añadirlo al proyecto
