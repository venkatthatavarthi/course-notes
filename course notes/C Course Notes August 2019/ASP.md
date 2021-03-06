# ASP

# ASP Core Website With Entity

Let's move our learning forwards.

    Critical learning for the course
    
    	Basic HTML/CSS ==> done (enough)
    	Javascript : minimal
    		(upgrade)
    	Bootstrap  : need to play around with
    	Entity with LINQ : done apart from advanced LINQ
    	Entity Core : started today
    	Generating and migrating databases : minimal today ==> can do more
    	API : started
    	ASP : simple website
    	MVC : done a good bit, can develop

New ASP site v 2.1 and EFCore libraries 2.1.1

### Adding libraries using Powershell

dotnet add package microsoft.entityframeworkcore -v 2.1.1
.sqlserver
.sqlite
.design

### Adding pages

Note

    ASP WEB ==> 2 files per page     .cshtml  as root
    								 .cshtml.cs  with raw c# code 'behind' the page
    
    MVC     ==> 1 file per page      .cshtml
    
    Shared\\_Layout   page   has all of the shared layout
    
    _ means private ie cannot view this page directly; only via another page
    
    Startup.cs
    	Set basis for website
    	Install all libraries
    	Can configure global access to database (later on for our learning 'injecting
    			context' from database into our app)
    
    UseStaticFiles()
    
    	wwwroot global folder with all non-secure data
    		CSS
    		IMAGES
    		JS LIBRARIES EG BOOTSTRAP
    
    Database Connection Strings
    
    	1) App.Config (core only)
    	2) Web.Config                 older 
    	3) appsettings.json 	      newer
    
    Pages
    	index.cshtml
    	..
    
    Models
    	Customer.cs
    	..
    
    C# in webpage is called RAZOR
    
    @page required first line ==> RAZOR PAGE otherwise RAW HTML
    
    @model refers to DATA IN C# TWIN PAGE
    
    @Model is used in RAZOR to access data
    
    ViewData/ViewBag are ARRAY OF STRINGS to push trivial data on any page