# REST API

# Rest API
    
    <pre>
    	 
    REST was invented in 2000 by Roy Fielding at University of California.  It has displaced SOAP and other XML-based methods of obtaining information because of its ease of use.
    REST uses HTTP to transfer data.
    REST is STATELESS (no knowledge of previous or future transactions ie each transaction is completely standalone)
    REST exposes data using directory structure inside a URL www.mydomain.com/getdata/1  will get record 1
    REST can transfer XML or JSON data.
    Examples of certain public websites which off APIs for public use can be found here
    
        https://apigee.com/console/google-spreadsheets
        https://www.programmableweb.com/APIS/DIRECTORY
        https://www.programmableweb.com/category/all/apis
        https://apigee.com/console/instagram
    
    REST API Video Tutorials
    
    Here is an 8-minute overview video of what an API is and can do.  
    It was released in 2014 so what worked then no longer works now, 
    but it's useful anyway as a primer with some striking examples 
    of what can be done with public APIs 
    (note : the public APIs talked about have since added stricter authentication 
    so you can't copy exactly some of the stuff talked about - you first have to 
    now obtain an OAUTH TOKEN to use these websites)
    https://www.youtube.com/watch?v=7YcW25PHnAA
    Here is a video tutorial of building a REST API with Node and Mongo
    https://www.youtube.com/watch?v=Do_Hsb_Hs3c (22 minutes)
    BUILD A RESTFUL API FROM SCRATCH WITH NODE AND MONGO
    https://www.youtube.com/watch?v=eB9Fq9I5ocs  (1 hour long video)
    	
    	
    	
    Examples Of REST APIs
    
    
    Google Maps
        maps.googleapis.com/maps/api/geogode/json?latlng=51.5014893,-0.0005504
        
        maps.googleapis.com/maps/api/geocode/json?address=fort%20william
    
    Instagram
        
    
        
    api.instagram.com/v1/media/search
    
        
    api.instagram.com/v1/media/search?lat=x&lng=y&distance=z
    
    	
    
    
        
    Twitter
        
    
        
    https://api.twitter.com/1.1/statuses/update.json 		
    	
    	POST USING POSTMAN AND OAUTH
    
    			
    
    		
    
    API Example - using Facebook API
        
    
        
    https://developers.facebook.com/apps
    
        
    CREATE AN APP FOR YOUR WEBSITE
    
        
    NOW PASTE IN DETAILS INTO 
    
    			https://graph.facebook.com/oauth/access_token?client_id=APP_ID&client_secret=APP_SECRET&grant_type=client_credentials
    
    
    	
    		
        
    Facebook ID findmyfbid.com
    
        
    Facebook Graph 
    	Embed Facebook photos and posts
    		
    	http://graph.facebook.com/youtube      Error : OAuthException : Access token is required to access this resource
    		
    	http://graph.facebook.com/youtube?fields=id,name,likes
    
    
    
    REST provides a 1-1 mapping with the basic CRUD operations Create, Read, Update, Delete with paths in a URL
    	- GET reads data
    	- POST adds data
    	- PUT updates data
    	- DELETE deletes data
    	
    		
    </pre>