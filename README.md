# NetConf2025.PassKeysDemo

Pass keys demo with .NET 10 for Dotnetters

## Database (SQL Server) with Docker

Start a SQL Server instance using Docker Compose (background):

```powershell
docker compose up -d
```

The project expects a SQL Server available at the connection string in `NetConf2025.PassKeysDemo.WebApp/appsettings.json` (DefaultConnection). The included sample uses `Server=localhost,1433;Database=PassKeysDemoDb;User Id=sa;Password=Soy_Feliz_1234;TrustServerCertificate=True;`.

If you prefer to run the official container manually instead of `docker compose`, you can run:

```powershell
docker run --rm -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Soy_Feliz_1234" -p 1433:1433 mcr.microsoft.com/mssql/server:2022-latest
```

## Applying EF Core migrations

From the repository root, apply migrations to the database with:

```powershell
dotnet ef database update --project NetConf2025.PassKeysDemo.WebApp --startup-project NetConf2025.PassKeysDemo.WebApp
```

This will create the `PassKeysDemoDb` database and apply the generated migrations.

## Run the application

To run the web application locally:

```powershell
dotnet run --project NetConf2025.PassKeysDemo.WebApp
```

Then open your browser at the URL printed by the application (usually `https://localhost:5001` or similar).

## Authors

- Cristian Garrido Méndez — https://github.com/cgarrido
- Illari Alvarez-Gil Escobar — https://github.com/IllariLaksmi

