Author: Aarsal Masoodi
Date Created: November 1st, 2021

Date Modified: November 3rd, 2021

I created a project through Visual Studio 2019. It was through an ASP.NET Core Web App (Model-View-Controller) template.
I explored the defaulty created Models, Views, and Controllers. 
I reviewed the other default files as well, such as the IActionResult that takes me to the various navigations and returns the View.

I experimented with debugging and creating break points at the home controller page.

I chose a different bootstrap theme through the website Bootswatch.com. The theme I chose is called "Solar".
I replaced the bootstrap.min.css file under the wwwroot/lib/boostrap/dist/css folders. 
I replaced the site.css found under wwwroot/css with a file I obtained from blackboard.

I changed various properties in the project, such as making the nav class have a dark nav bar instead of white.
I added several additional scripts that I will use in the site. I added them to the bottom of the _Layout.cshtml page.

I created 3 new projects, which were .Net Core class library projects. I then copied the Data folder from the main project into the AarsalsBooks.Data class library.
I installed two packages through the NuGet installer built into visual studio 2019. EntityFramework Core.Relational and Core.SqlServer.

I then deleted the migrations folder, inside the data folder. 

_________________________________________________________________________________________________________________________________________________________

Nov 3rd, 2021
I was unable to get the projects working, so I loaded in an older repository to try again.
Realized I missed a change on the startup.cs file, so I did it now. I deleted the sign in requirements command. 

I experimented with debugging again. After I create the breakpoint, I need to use the "continue" button in visual studio to go to the next break point.
I went through the process of adding a new theme from bootswatch.com again. Deleted references to text-dark, changed some of the properties on the layout and loginpartial pages.
Went through and added the code for the dropdown menu again. And once again, it's not toggling. I'm not entirely sure what I've missed.

I added three library class projects to the solution. AarsalsBooks.DataAccess, AarsalsBooks.Models and AarsalsBooks.Utility.
I moved the data folder into the DataAccess class library. 
I added two packages to the DataAccess class library, EntityFrameworkCore Relational and SqlServer
I then deleted the migrations folder in the same class library, under the data folder. 
I changed the namespace in the data folder to match the library class. 

So I finally was able to build without problems! I had to change the Error.cshtml models name to reference my models class library. 
I created a static class called SD.cs in the utility project. I then added project references for this to the main project, and also to the DataAccess class library. 
I added a new area called "Customer" and changed the route pattern in startup.cs to reference the area.

_________________________________________________________________________________________________________________________________________________________
Starting up part 2 of the assignment.

First thing I did was build the solution to make sure it was working. I kept getting only "4 up-to-date" rather than build succeeded, so I did rebuild and then build and it worked.
I'm reviewing the appsettings.json file, and I changed the name of the database. 
I used the NuGet package manager to add the migration. The migration file name is: 20211206223139_AddDefaultIdentityMigration
I  updated the database with the "update-database" command in the PM console. 

I added a new table to the database by creating the category model class. This class creates the table. 
I added the migration but the new migration file was empty. To fix this I modified the ApplicationDbContext.cs file.
I then deleted the old migration and migrated the new class again. Then I updated the database. 

Now we need to create a repository. I created a new folder in the DataAccess project called Repository, then another folder called IRepository inside of that one.
I added an interface type item called IRepository and modified it to be used for CRUD operations on the Category class.

After added the CRUD elements to that interface above, I created a new class in the Repository folder called Repository.cs. I implemented the interface that I had made earlier with this class.
Using the provided repository file, I filled in the CRUD methods. There were templates given to me after I interfaced the class.
I created a class and an interface class for the Category table specifically, though the interface class could also be used for other potential models. 
I added the update method for this class.

Created a new interface class called ISP_Call. This will be used to map multiple repositories in a Unit of Work. 
I had to install the Dapper package to extend the IDisposable class and use its methods such as DynamicParameters. 
After creating the interface, I used it to extend a new class, SP_Call.cs. I then populated the template created with the correct methods. 

I added a new interface, this time called IUnitOfWork to the IRepository folder. 
I used that interface to build a new class UnitOfWork. I added code to make it accessible to the project in the Startup.cs file. 
I was having errors with accessibility. I fixed this by setting both interface classes as public. 

I added the CategoryController in the Admin area. This controller uses the IUnitOfWork interface. In the same Admin area, I created a new Index view. 
I modified the generic index code with html given to me. I then both added the category menu item and then move it into the dropdown menu I had created before. 


