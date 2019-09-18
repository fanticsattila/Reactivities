# Reactivities
Complete guide to building an app with .Net Core and React by Neil Cummings

Előkészületek:
- .NET Core 2.2 SDK
	https://dotnet.microsoft.com/download/dotnet-core
- Visual Studio Code
	https://code.visualstudio.com/Download
	Telepítendő plugin-ek:
		- Auto Close Tag
		- Auto Rename Tag
		- Auto-Using for C# *
		- Bracket Pair Colorizer 2
		- C#
		- C# Colors *
		- C# Extensions
		- ES7 React/Redux/GrapQL/React-Native snippets 
		- Material Icon Theme
		- NuGet Package Manager
		- Prettier - Code formatter
		- Prettify JSON *
		- SQLite
		- vscode-database *

- NodeJs
	https://nodejs.org/en/
  Újraindítás szükséges utána
	Tesztelése Powershell-ben:
		node -v
		npm -v

- Git
	https://git-scm.com/download/win

- Postman
	https://app.getpostman.com/app/download/win64

Parancssori utasítások:

Section 2 - Walking Skeleton Part 1 - API

	- Dotnet elérhetőségének vizsgálata
		dotnet --version
	
	- Főkönyvtár létrehozása
		md Reactivities
		cd Reactivities
	
	- Solution fájl létrehozása
		dotnet new sln
	
	- Projektek létrehozása
		dotnet new classlib -n Domain
		dotnet new classlib -n Application
		dotnet new classlib -n Persistence
		dotnet new webapi -n API

	- Projektek hozzáadása a Solution-hoz
		dotnet sln add Domain/
		dotnet sln add Application/
		dotnet sln add Persistence/
		dotnet sln add API/

		Ellenőrzése:
		dotnet sln list

	- Projekt referenciák létrehozása
		cd Application/
		dotnet add reference ../Domain/
		dotnet add reference ../Persistence/
		cd ..
		cd API
		dotnet add reference ../Application/
		cd ..
		cd Persistence
		dotnet add reference ../Domain/
		
	- Projekt futtatása (Reactivities könyvtárból)
		dotnet run -p API/
	
	- Entity Framework hozzáadása Persistence projekt-hez
		Ctrl+Shift+P -> nuget -> Add NuGet Package
		Microsoft.EntityFrameworkCore
		Microsoft.EntityFrameworkCore.Sqlite

	- Entity migration:
		dotnet ef migrations add InitialCreate -p Persistence/ -s API/

	- Entity migration automatikus futtatása induláskor:
		Program.cs-ben!

	- Projekt debug futtatása:
		cd API/
		dotnet watch run

	- Adatok seed-elése az adatbázisba
		DataContext.cs-ben OnModelCreating ÉS
		dotnet ef migrations add SeedValues -p Persistence/ -s API

		

