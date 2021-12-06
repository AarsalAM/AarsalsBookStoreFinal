﻿Author: Aarsal Masoodi
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