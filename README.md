# Noir Essence – Backend REST API

**Noir Essence** este un proiect e-commerce dedicat comercializării parfumurilor, dezvoltat ca aplicație **backend REST API** folosind **C# și ASP.NET Core**.  
Scopul proiectului este implementarea unui server **modern, scalabil și ușor de întreținut**, care gestionează funcționalitățile principale ale unui magazin online.

### Funcționalități implementate

### Gestionare Categorii (CRUD)
- `GET /api/Category` – listare categorii
- `GET /api/Category/{id}` – detalii categorie
- `POST /api/Category` – creare categorie
- `PUT /api/Category/{id}` – modificare categorie
- `DELETE /api/Category/{id}` – ștergere categorie  
  > O categorie nu poate fi ștearsă dacă are produse asociate.
###  Gestionare Produse (CRUD)
- `GET /api/Product` – listare produse
- `GET /api/Product/{id}` – detalii produs
- `POST /api/Product` – creare produs
- `PUT /api/Product/{id}` – modificare produs
- `DELETE /api/Product/{id}` – ștergere produs  
  Produsele sunt asociate unei categorii prin relație **One-to-Many (Category → Products)**

### Utilizatori & Autentificare
- `POST /api/Auth/register` – înregistrare utilizator
- `POST /api/Auth/login` – autentificare utilizator
- Autentificare bazată pe **JWT (JSON Web Token)**
- Parolele sunt stocate securizat folosind **hashing (PasswordHasher)**

## Data Transfer Objects (DTO)
DTO-urile sunt utilizate pentru:
- separarea entităților de baza de date de datele expuse prin API
- creșterea securității (ex: parolele nu sunt expuse)
- validarea datelor de intrare

Exemple:
- `ProductCreateDto`, `ProductUpdateDto`, `ProductReadDto`
- `CategoryCreateDto`, `CategoryUpdateDto`
- `RegisterDto`, `LoginDto`, `AuthResponseDto`

## Bază de date
- **PostgreSQL**
- Acces la date realizat prin **Entity Framework Core**
- Migrațiile EF Core sunt folosite pentru versionarea bazei de date
  
## Securitate & Configurare
- Datele sensibile (connection string, JWT key) **nu sunt stocate în repository**
- Configurația este gestionată prin:
  - **User Secrets** (local development)
  - **Environment Variables** (deploy / runtime)
- Repository-ul este protejat prin `.gitignore`

## Rulare locală
Cerințe:
- .NET SDK
- PostgreSQL
- Git

Pași:
bash
dotnet restore
dotnet run


