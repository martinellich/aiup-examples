# Hotel Reservation System - Requirements Catalog

## Project Overview

A web-based hotel reservation system that allows guests to search, book, and manage hotel room reservations. The system
supports hotel staff in managing bookings, room availability, and guest services.

## Functional Requirements

| ID     | Requirement             | Description                                                                                             | Priority |
|--------|-------------------------|---------------------------------------------------------------------------------------------------------|----------|
| FR-001 | Room Search             | Guests can search for available rooms by check-in date, check-out date, number of guests, and room type | High     |
| FR-002 | Room Booking            | Guests can reserve available rooms by providing personal details and payment information                | High     |
| FR-003 | Booking Confirmation    | System sends booking confirmation with reservation details via email                                    | High     |
| FR-004 | Booking Management      | Guests can view, modify, or cancel their existing reservations                                          | Medium   |
| FR-005 | Room Inventory          | Hotel staff can add, update, and remove room information including type, capacity, and amenities        | High     |
| FR-006 | Availability Management | Hotel staff can view and update room availability for specific dates                                    | High     |
| FR-007 | Guest Check-in          | Hotel staff can check in guests and assign specific room numbers                                        | High     |
| FR-008 | Guest Check-out         | Hotel staff can process guest check-out and generate final bills                                        | High     |
| FR-009 | Payment Processing      | System processes credit card payments for reservations                                                  | High     |
| FR-010 | Pricing Management      | Hotel staff can set and update room rates based on seasons and demand                                   | Medium   |
| FR-011 | Guest Profile           | System maintains guest profiles with contact details and booking history                                | Medium   |
| FR-012 | Reporting               | Hotel staff can generate reports on occupancy, revenue, and booking statistics                          | Medium   |
| FR-013 | Room Status Updates     | Hotel staff can update room status (clean, dirty, maintenance, out of order)                            | Medium   |
| FR-014 | Booking Notifications   | System sends reminder emails to guests before check-in date                                             | Low      |

## Non-Functional Requirements

| ID      | Requirement       | Description                                                    | Metric                                          | Priority |
|---------|-------------------|----------------------------------------------------------------|-------------------------------------------------|----------|
| NFR-001 | Response Time     | System responds to user requests within acceptable time limits | < 1 seconds for search, < 2 seconds for booking | High     |
| NFR-002 | Availability      | System is available for booking operations                     | 99.5% uptime during business hours              | High     |
| NFR-003 | Concurrent Users  | System supports multiple simultaneous users                    | Up to 50 concurrent users                       | Medium   |
| NFR-004 | Data Security     | Guest personal and payment data is protected                   | SSL encryption                                  | High     |
| NFR-005 | Mobile Responsive | System adapts to different screen sizes                        | Responsive design for tablets and smartphones   | Medium   |
| NFR-006 | Data Backup       | Regular backup of reservation and guest data                   | Daily automated backups with recovery testing   | High     |
| NFR-007 | User Interface    | System provides intuitive and user-friendly interface          | Usability testing with target users             | Medium   |
| NFR-008 | Scalability       | System can handle growth in bookings and users                 | Support for 200% increase in current load       | Low      |

## Constraints

| ID      | Constraint             | Description                                                    | Type      | Impact                                |
|---------|------------------------|----------------------------------------------------------------|-----------|---------------------------------------|
| CON-001 | Technology Stack       | Must use Vaadin, Spring Boot, and jOOQ                         | Technical | Development approach and architecture |
| CON-002 | Database               | Must use PostgreSQL database                                   | Technical | Data storage and query design         |
| CON-003 | Accessibility          | Must meet basic web accessibility standards (WCAG 2.1 Level A) | Legal     | UI design and implementation          |
| CON-004 | Multi-language Support | System supports German, French, Italian, and English languages | Low       | Attractiveness to users               |

