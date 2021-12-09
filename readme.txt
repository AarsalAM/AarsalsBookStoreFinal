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

To experiment with Font Awesome icons, I added them using element classes in the index file for category. I am now going to delete that and instead use the given javascript files.
In these given javascript files, the same Font Awesome is used.

I created an Upsert action result in the Category Controller. I also added an Upsert page as a view.
I then created a partial view for both edit and back.

I populated the Upsert.html and tested it. I then changed something on the page while the app was still running and refreshing the page showed my change of adding the title.
I added a @section to validate the input.

I created an Upsert POST action method in the Category Controller.
I added a void save method to the category repository to add the save method. 
I tested and was able to create and update categories without issue.

I am now adding the delete functionality. 
I added the delete API to the CategoryController.cs page. 

I then created a delete function in the category.js script file. I added the onclick functionality in trhe file as well.
As it was said not to work on MS edge, I changed the browser to chrome.
I tested but the delete function was not working. Troubleshooting now.
Was able to find the error. I was missing a closing parenthesis in the onclick delete event. As well as a space before the class declaration. 
I had another error, the table would not auto reload when deleted. 
This was caused by a typo in the word "success". I found it and fixed it, it now all works.

This is the end of part 2.


_________________________________________________________________________________________________________________________________________________________
Assignment 2 - Part 3 (section 1)

First thing to do is create Cover Type CRUD. I am to do this by following the exact same steps used to create Category CRUD previously. 
I first created the CoverType.cs model, in the models folder. This one also has an ID and a Name.
I then added the CoverType to the ApplicationDbContext.cs file, and then pushed a migration to the database.
the name of the migration file is: 20211209160632_AddCoverTypeToDb.cs
I update the database.
I then created an interface and a class for the CoverType in the repository folders. 
I added the appropriate code so that it replicates the Category model and interfaces. 
I added the CoverType code into the UnitOfWork files as well
When adding the code into the UnitOfWork file, I have a cast error. Troubleshooting that now.
found it, had category instead of covertype when making a reference. 
I added the cover type controller and views. I gave it CRUD functionality and created a new js file for it as well.
The cover type page is working.

So now we're working on a new page, the Products page. I created a Product.cs model with the provided code.
I added the reference to the product page in the database, in the ApplicationDbContext.cs file.
I then used the migration command. The Name of the file is: 20211209200459_addProductToDb
I updated the product class to make Title, ISBN, and  Author required. I then created a new migration.
20211209200659_addValidationToProduct.cs
I added Product to the repository, as well as created the IProductRepository interface and class.
I remembered to put the correct using statements at the top.
I implemented the interface I created, then updated the Update method for the Product class.

I created a Product Controller in the Admin area. 
I added the IWebHostEnvironment call.
Added a Product ViewModel class and put it in the ViewModels folder.
I had to install the Microsoft.AspNetCore.Mvc.ViewFeatures package to be able to use the <SelectListItem> part of the code.
I added to the Product Controller and created the Upsert method. Though I have it commented out for now.
I updated the API call to include the Category and CoverType properties. 
I added a folder to the views area under admin, folder called Product. 
Created the index page and changed the layout of the table. Created a new .js file as well with some modifications. 
I added the page to the last open area in the drop down menu navbar.

Finally, will be adding the Upsert.cs page.
The code for the page was provided. I created an account at tiny.cloud and was given an API key. I added it to the scripting at the bottom.
I used it to add a rich textbox to the textarea, as well as to validate input.