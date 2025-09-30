# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hotel Reservation System - A web-based hotel reservation system built with Spring Boot 3.5.4, Vaadin 24.8, and jOOQ for database access. The application enables guests to search, book, and manage hotel room reservations while supporting hotel staff in managing bookings, room availability, and guest services.

## Technology Stack

- **Framework**: Spring Boot 3.5.6 with Java 21
- **UI**: Vaadin 24.9 (Flow-based Java UI framework)
- **Database Access**: jOOQ
- **Database**: PostgreSQL 
- **Database Migration**: Flyway
- **Build Tool**: Maven (use `./mvnw` wrapper)
- **Monitoring**: Spring Boot Actuator

## Key Commands

### Development
```bash
# Run the application in development mode
./mvnw spring-boot:run

# Run tests
./mvnw test

# Run a single test class
./mvnw test -Dtest=HotelReservationSystemApplicationTests

# Clean and build
./mvnw clean package

# Build for production (includes Vaadin frontend optimization)
./mvnw clean package -Pproduction
```

### Database
```bash
# Flyway migrations run automatically on application startup
# Migration files should be placed in src/main/resources/db/migration/

# To run migrations explicitly
./mvnw flyway:migrate

# To get migration info
./mvnw flyway:info
```

## Architecture

### Package Structure
Base package: `ch.martinelli.demo.hrs`

The project follows a standard Spring Boot structure with:
- Main application class: `HotelReservationSystemApplication.java`
- Resources in `src/main/resources/`
- Tests in `src/test/java/`

### Vaadin UI
- This is a Vaadin Flow application (Java-based views, not Hilla/React)
- Vaadin UI components are server-side rendered
- Development mode automatically opens browser (`vaadin.launch-browser=true`)
- Production builds require the `production` profile to optimize frontend assets

### Database Access
- Uses jOOQ for type-safe SQL queries
- jOOQ code generation should be configured to run against PostgreSQL schema
- Flyway manages database schema migrations

### Configuration
Application configuration in `src/main/resources/application.properties`:
- Application name: `hotel-reservation-system`
- Vaadin launches browser automatically in dev mode

## Requirements
Functional and non-functional requirements are documented in German in `docs/requirements/requirements_catalog.md`, including:
- Guest features: room search, booking, booking management
- Staff features: room management, availability management, check-in/out, reporting
- System requirements: performance (1s search, 2s booking), 99.5% availability, 50 concurrent users
- Constraints: Must use Vaadin, Spring Boot, jOOQ, and PostgreSQL; must support DE/FR/IT/EN languages

## Development Notes

### Vaadin Development
- When working with Vaadin Flow components, use Java classes extending `VerticalLayout`, `HorizontalLayout`, or implementing `RouterLayout`
- Views are annotated with `@Route`
- For Vaadin-specific questions, consult the Vaadin MCP server available in this environment

### jOOQ Integration
- jOOQ provides type-safe database access
- Generated jOOQ classes should be regenerated when database schema changes
- For jOOQ-specific questions, use the jOOQ MCP server available in this environment

### Database
- PostgreSQL is the required database
- Use Flyway for all schema changes (create migration files in `src/main/resources/db/migration/`)
- Follow naming convention: `V{version}__{description}.sql`