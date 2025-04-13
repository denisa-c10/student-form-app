# student-form-app
# Student Form API

Aceasta este o aplicație care permite completarea unui formular de înscriere al unui student, care include detalii precum nume, prenume, facultate și motivul pentru care se înscriu. După completarea formularului, aplicația generează un PDF care conține aceste informații. (dupa multe incercari si erori nu am reusit sa generez PDF-ul, desi am verificat codul de foarte multe ori, la fel si instalarile)

Proiectul este împărțit în două părți:
- **Frontend**: O aplicație Angular care trimite datele formularului către API-ul backend.
- **Backend**: O aplicație .NET Core care primește datele, le salvează într-o bază de date și generează un PDF folosind DinkToPdf.

## Tehnologii folosite

- **Frontend**: Angular
- **Backend**: .NET Core
- **PDF Generation**: DinkToPdf / wkhtmltopdf
- **Database**: SQL Server (Entity Framework)

## Instalare locală

### Pasul 1: Clonarea repository-ului

Clonarea repository-ului pentru backend și frontend:

```bash
git clone https://github.com/user/student-form-api.git
cd student-form-api

dotnet restore
dotnet ef database update
dotnet run

## Pasul 2: Instalarea Frontend (Angular)

1. Deschide proiectul frontend în Visual Studio Code.
2. Instalează dependențele necesare cu comanda:

   ```bash
   npm install
ng serve
Detalii despre endpoint-uri:
1. Endpoint-ul pentru crearea formularului și generarea PDF-ului
Metodă: POST

URL: http://localhost:5200/api/forms

Body:

json
Copy
Edit
{
  "nume": "Denisa",
  "prenume": "Coman",
  "facultate": "Științe Economice",
  "motivatie": "Motivație lungă..."
}
Răspuns: Dacă formularul a fost procesat cu succes, va returna un PDF cu numele Fisa_Student_Denisa_Coman.pdf.

2. Endpoint-ul pentru obținerea tuturor formularelor
Metodă: GET

URL: http://localhost:5200/api/forms

Răspuns:

json
Copy
Edit
[
  {
    "id": 1,
    "nume": "Denisa",
    "prenume": "Coman",
    "facultate": "Științe Economice",
    "motivatie": "Motivație lungă...",
    "dataSubmisiei": "2025-04-13T14:00:00"
  },
  ...
]

3. Endpoint-ul pentru obținerea unui formular după ID
Metodă: GET

URL: http://localhost:5200/api/forms/{id}

Răspuns:

json
Copy
Edit
{
  "id": 1,
  "nume": "Denisa",
  "prenume": "Coman",
  "facultate": "Științe Economice",
  "motivatie": "Motivație lungă...",
  "dataSubmisiei": "2025-04-13T14:00:00"
}

4. Endpoint-ul pentru actualizarea unui formular
Metodă: PUT

URL: http://localhost:5200/api/forms/{id}

Body:

json
Copy
Edit
{
  "id": 1,
  "nume": "Denisa",
  "prenume": "Coman",
  "facultate": "Științe Economice",
  "motivatie": "Motivație actualizată..."
}

5. Endpoint-ul pentru ștergerea unui formular
Metodă: DELETE

URL: http://localhost:5200/api/forms/{id}

