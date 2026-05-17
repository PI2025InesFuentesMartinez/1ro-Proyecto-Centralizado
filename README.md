# Proyecto Intermodular — Sistema de Gestión de Reservas

**Autora:** Inés Fuentes Martínez
**Ciclo:** Desarrollo de Aplicaciones Web (DAW)
**Curso:** 1º DAW — 2025/2026

---

## Sobre este repositorio

Este repositorio **no es un proyecto al uso** con un único código que se descarga y se ejecuta, sino un **repositorio centralizado** donde se recogen todas las entregas que he ido realizando a lo largo del curso en las distintas asignaturas (módulos) del ciclo, y que en conjunto conforman mi **Proyecto Intermodular**.

La idea del Proyecto Intermodular es que las entregas de varias asignaturas no sean ejercicios aislados, sino piezas de un mismo proyecto: un **sistema de gestión de reservas de recursos** (salas, laboratorios, aulas, instalaciones, etc.). Cada entrega aporta una capa distinta, base de datos, diseño web, programación, documentación de API, copias de seguridad, etc. y todas ellas se integran aquí en un único repositorio para poder consultarlas de forma conjunta.

> **Nota sobre la temática:** Por el momento aún no se nos ha permitido fijar la temática concreta del proyecto, así que el dominio se trabajó de forma **deliberadamente genérica** (con términos como "Recurso" en lugar de algo más específico).

---

## Tema del proyecto

**Sistema de Gestión de Reservas de Recursos.**

Un sistema que permite a usuarios reservar recursos (salas, aulas, laboratorios, instalaciones deportivas…) en franjas horarias, gestionando:

- Usuarios (con dos roles: Administrador y Usuario Normal).
- Recursos y sus horarios de disponibilidad.
- Reservas con validaciones de fechas, plazas y solapamientos.

El modelo se ha mantenido durante todo el curso, de modo que la base de datos diseñada en UP2 es la misma que se ha implementado físicamente en SQL, se ha consumido desde la API documentada en UP9 y se ha utilizado como soporte del CRUD en Java desarrollado en UP12.

---

## Entregas incluidas en este repositorio

Las entregas listadas a continuación son las mismas que se muestran en [src/landing_page/index.html](src/landing_page/index.html), pensada como página de aterrizaje del proyecto.

| UP | Asignatura | Entrega | Ubicación |
|----|------------|---------|-----------|
| UP2 | BD | Modelo Entidad/Relación | [database/diagram E-R/](database/diagram%20E-R/) |
| UP4 | SI | Instalación del entorno de trabajo con XAMPP | [docs/XAMPP/](docs/XAMPP/) |
| UP4 | BD | Diseño lógico — Modelo relacional | [database/relational model/](database/relational%20model/) |
| UP5 | EDE | Repositorio de GitHub | Este propio repositorio |
| UP5 | BD | Diseño físico — Modelo físico en SQL | [database/scripts/](database/scripts/) |
| UP6 | LMSGI | Web Consultora — HTML + CSS | [proyecto-consultora/](proyecto-consultora/) |
| UP9 | LMSGI / PI | Diseño de API REST para el sistema de reservas | [docs/api/](docs/api/), [docs/diagrams/](docs/diagrams/), [docs/disaster-recovery/](docs/disaster-recovery/) |
| UP10/11 | SI | Copia de seguridad colaborativa en NAS | [database/backups/](database/backups/) |
| UP12 | PROG | CRUD de Reservas (Java + JDBC + MVC) | [src/app/](src/app/) |
| Final | — | Defensa del Proyecto Intermodular | [ENTREGA FINAL (defensa)/](ENTREGA%20FINAL%20(defensa)/) |

---

## Estructura del repositorio

```
Proyecto-Centralizado/
├── README.md                       ← este documento
│
├── database/                       ← Entregas del módulo de Base de Datos
│   ├── diagram E-R/                  · UP2: Modelo E/R + vídeo de defensa
│   ├── relational model/             · UP4: Diseño lógico (modelo relacional)
│   ├── scripts/                      · UP5: Script SQL de creación + inserts
│   └── backups/                      · UP10/11: Documento de copias de seguridad en NAS
│
├── docs/                           ← Documentación transversal
│   ├── XAMPP/                        · UP4 SI: Instalación del entorno XAMPP
│   ├── api/                          · UP9: Diseño de la API REST
│   │   ├── 1-analisis-dominio/         · Análisis de dominio + capturas Swagger UI
│   │   ├── 2-ejemplos-json/            · Ejemplos JSON de request / response
│   │   └── 3-openapi/                  · Especificación OpenAPI 3.0 + Swagger UI estático
│   ├── diagrams/                     · UP9: Diagramas de la API
│   └── disaster-recovery/            · UP9: Plan de recuperación ante desastres
│
├── proyecto-consultora/            ← UP6 LMSGI: Web consultora "Astro"
│   ├── index.html · cronologia.html · proyecto-reservas.html · contacto.html
│   ├── css/  ·  img/
│   └── README.md                     · Memoria de la entrega (paleta, decisiones, retos)
│
├── src/
│   ├── landing_page/               ← Página de aterrizaje del proyecto intermodular
│   │   └── index.html                · Índice visual con todas las entregas
│   │
│   └── app/                        ← UP12 PROG: CRUD en Java
│       ├── pom.xml                   · Proyecto Maven (Java 21 + MariaDB JDBC)
│       ├── README.md                 · Memoria técnica del CRUD
│       └── src/main/java/com/reservas/
│           ├── app/                  · Main
│           ├── model/                · Modelos (Usuario, Administrador, UsuarioNormal,
│           │                           Recurso, Horario, DisponibleEn, Reserva)
│           ├── dao/                  · Acceso a BD (patrón DAO + Singleton de conexión)
│           ├── view/                 · Menús por consola
│           └── controller/           · Controladores, Coordinación Vista ↔ DAO (patrón MVC)
│
└── ENTREGA FINAL (defensa)/        ← Material de defensa final del proyecto
```

---

### Entrega final — Defensa
Material de la defensa final del proyecto intermodular: documento de acompañamiento al vídeo y enlace al vídeo de defensa ([ENTREGA FINAL (defensa)/](ENTREGA%20FINAL%20(defensa)/)).

---

## Tecnologías utilizadas a lo largo del proyecto

- **Base de datos:** MariaDB / MySQL (sobre XAMPP).
- **Modelado:** Modelo E/R y modelo relacional.
- **Frontend (UP6):** HTML5 semántico + CSS3 (Flexbox, Grid, media queries, variables CSS, Google Fonts — Inter).
- **API (UP9):** OpenAPI 3.0 + Swagger UI.
- **Backend (UP12):** Java 21, Maven, JDBC, patrón MVC + DAO + Singleton.
- **Control de versiones:** Git + GitHub.
- **Entorno:** XAMPP (Apache + MariaDB).

---

## Autoría

Todo el contenido de este repositorio ha sido elaborado por **Inés Fuentes Martínez** como parte del Proyecto Intermodular de 1º DAW del curso 2025/2026.
