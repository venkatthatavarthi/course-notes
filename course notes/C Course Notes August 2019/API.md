# API

# Web !!!

Web realm is incredibly exciting

    Check out BLAZOR which is C# natively running in Browser.
    
    Today we are going to check out APIs which power much of the web.
    
    Website 										HUMAN CONSUMPTION 	 HTML structure
    																	 CSS colour, animations
    																	 JAVASCRIPT code
    
    API  (Application Programming Interface) 		MACHINE CONSUMPTION  DATA in form of
    																		1) JSON 
    																		2) XML  
    
    JSON 
    {
       "field":value,
       "field":value
    }
    
    [
    	{
    	   "field":value,
       		"field":value
    	},
    	{
    	   "field":value,
       		"field":value
    	}
    ]
    
    
    XML
    <rootElement>  										< >  Tag , Element  ((ONE ROOT ONLY))
    	<item length="1">                               Element with Attribute (length) and Value (1)
    		<field otherValue="admin">Value</field>
    	</item>
    </rootElement>

Goal

    1) Northwind
    2) Entity Framework
    3) Scaffold API from scratch with minimal work

MVC Methodology

    Model  		Database Item  ==> C#     Class matches database Table
    									  Northwind Customers ==> Class Customer
    
    
    View 		Display of data to end user : HTML/CSS/Javascript + server-side data fed into page
    										   (translated into HTML/CSS/Javascript)
    
    
    			Server                           		    Client
    			C#/Node/PHP/Java/Python/Ruby
    				Render
    				    Translate raw data into
    				    form suitable for viewing
    				    ie HTML etc    ================>>>Sent to client for display=====>
    
    Controller  look at URL to make sense of it
    
    				<https://www.mydomain.com/controller/action/id>
    
    					                    /customers/Get/           SELECT *
    					                    /customers/Get/ALFKI      SELECT .. where id=ALFKI
    					                    /customers/Post/          NEW 
    					                    /customers/Post/id        UPDATE
    					                     could be /Put/id 		  UPDATE
    
    				GET : request VISIBLE IN URL
    				POST : 	request is INSIDE WEB PAGE DATA
    
    	Controller
    		a) Analyse URL
    		b) According to instructions in URL, go and get relevant data from Model
    		c) Send that data to a VIEW PAGE which display DATA

MVC Summary

    MODEL : DATA
    CONTROLLER : TAKE REQUEST AND RETURN DATA TO VIEW
    VIEW : DISPLAY

# API using .NET Core

Microsoft is strongly pushing .NET Core so let's use this opportunity to explore what it means to use .NET Core to read a database

Goals

1. 'Code First' approache to build our code, and from this to create a database

        a) SQLServer   
         b) SQLite      ==> try this way this time

2. Seed data from C# ie create new database with new data
3. Create API

# Setup

.Net Core 2.1 Web App with API

    Install libraries EntityFrameworkCore/SqLite/Design  v 2.1.1
    
    a) install-package ...     			NUGET
    b) dotnet add package ... 			POWERSHELL
    
    	dotnet add package microsoft.entityframeworkcore.design -v 2.1.1