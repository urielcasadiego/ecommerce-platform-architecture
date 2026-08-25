# KOOALITY — E-commerce Platform Architecture

KOOALITY es una plataforma de comercio electrónico *full-stack* diseñada con una arquitectura modular para la gestión de productos, la gestión de contenidos, la fijación de precios multidivisa/multipaís y las operaciones de comercio en línea.

Este repositorio presenta la arquitectura, las decisiones técnicas, los diagramas y ejemplos seleccionados (no destinados a producción) de la plataforma.

> El código fuente de producción es privado. Este repositorio contiene únicamente documentación del portafolio, diagramas de arquitectura y ejemplos depurados.
El proyecto sigue una arquitectura modular basada en dominios:

- Frontend Angular con rutas lazy-load
- SSR habilitado para renderizado del lado del servidor
- Apollo Angular para consumo de GraphQL
- Servicios de negocio y seguridad centralizados en core
- Features separadas por funcionalidad del negocio
- Autenticación con tokens JWT y refresh token

### Estructura principal

```text
src/
  app/
    app.config.ts
    app.routes.ts
    app.ts
    core/
    features/
    layout/
    shared/
```

## Stack tecnológico

- Angular 21
- Angular SSR
- RxJS
- Apollo Angular
- GraphQL
- Angular Material
- Firebase
- TypeScript

## Backend asociado

El frontend se comunica con el backend alojado en el repositorio hermano:

- [koality-backend](../koality-backend)

El backend está construido con:

- NestJS
- TypeScript
- GraphQL
- Prisma
- JWT + Passport
- PostgreSQL / ORM Prisma

## Arquitectura del frontend

### Capas principales

- Core: autenticación, idioma, país, navegación, sesión
- Features: auth, admin, products, profile, cart, home, legal, etc.
- Layout: shell, navbar, footer y estructura visual general
- Shared: componentes reutilizables y utilidades de UI

### Patrón de seguridad

La autenticación se maneja en el servicio AuthService, donde se persisten:

- accessToken
- refreshToken
- usuario actual
- metadata del país

Además, el cliente GraphQL agrega el token en cada petición y intenta refrescar sesión cuando el backend responde errores de autenticación.

## Configuración local

### Requisitos

- Node.js 20+
- npm
