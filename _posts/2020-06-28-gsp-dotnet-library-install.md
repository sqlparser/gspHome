---
layout: page
title: "Install and use the Genearl SQL Parser package using the dotnet CLI"
permalink: gsp-dotnet-library-install.html
categories:
  - how-to
  - gsp-dotnet
---

{% include toc %}

Install General SQL Parser package from www.nuget.org and once installed, refer to the package in code with using gudusoft.gsqlparser. You can then use the package's API.

### Prerequisites

- The [.NET Core SDK](https://www.microsoft.com/net/download/), which provides the command-line dotnet tool.

### Create a project

General SQL Parser packages can be installed into a .NET project of some kind. For this walkthrough, create a simple .NET Core console project as follows:

1. Create a folder for the project.
2. Create the project using the following command:

   _`dotnet new console`_
   
3. Use dotnet run to test that the app has been created properly.

   _`dotnet run`_


### Add the gudusoft.gsqlparser NuGet package

1. Use the following command to install [the gudusoft.gsqlparser package](https://www.nuget.org/packages/gudusoft.gsqlparser/): 

   _`dotnet add package gudusoft.gsqlparser`_
 
2. After the command completes, open the .csproj file to see the added reference:

   _`<ItemGroup> <PackageReference Include="gudusoft.gsqlparser" Version="3.2.6.5" /> </ItemGroup>`_
   
### Use the gudusoft.gsqlparser API in the app

1. Open the Program.cs file and add the following line at the top of the file:

   _`using gudusoft.gsqlparser;`_
   
2. Replace the Main function with the following:

	``` csharp
	static void Main(string[] args) {

		string sqlText = @"SELECT e.last_name AS name,
		e.commission_pct comm,
		e.salary * 12 ""Annual Salary""
		FROM scott.employees AS e
		WHERE e.salary > 1000 or 1=1
		ORDER BY
		e.first_name,
		e.last_name;";

		TGSqlParser sqlparser = new TGSqlParser(EDbVendor.dbvoracle);
		Console.WriteLine("versionId: "+ TBaseType.versionId);
		Console.WriteLine("releaseDate: "+TBaseType.releaseDate);
		 
		sqlparser.sqltext = sqlText;
		int ret = sqlparser.parse();
		if (ret == 0)
		{
			Console.WriteLine("Congratulations, you have successfully setup the general SQL parser.");
		}
		else
		{
			Console.WriteLine("Syntax error detected: {0}",sqlparser.Errormessage);
		}

	}
	```

3. Build and run the app by using the command

   _`dotnet run`_
   
   The output should be something like this:
   
   _`Congratulations, you have successfully setup the general SQL parser`_.
