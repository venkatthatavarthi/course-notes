# Loops

# Loops

4 loops

For
FIXED NUMBER OF LOOPS for(int i=0;i<=10;i++){}
GOOD WITH ARRAY BECAUSE GET INDEX AUTOMATICALLY i

    for(int i=0;i<array.length;i++){}

Foreach

    COLLECTION

While
while(x<10){}
may never execute

Do..While
do{}
while(x<10)
execute minimum one time

Break
Useful to avoid having nested loops

    // NESTED
    if(condition){
    	if(other condition){
    		if(otherothercondition){
    		    // code
    		}
    	}
    }
    
    
    public void DoThis(){
    	// USING BREAK
    	if(!condition)
    		break;
    	if(!othercondition)
    		break;
    	if(!otherothercondition)
    		break;
    	// code
    }
    
    Break will break out of a loop completely
    
    	foreach(var c in db.customers){
    		if(exitcondition){
    			break;
    		}
    	}
    	// start here

RETURN

    public string DoThis(){
    	// USING BREAK
    	if(!condition)
    		return 'null'
    	if(!othercondition)
    		return 'null'
    	if(!otherothercondition)
    		return 'null'
    	// code
    }

Continue
Finish this loop immediately and start next loop straight away
for(int i=0;i<10;i++){
// don't process 7
if (i==7){
continue;
}
// code
cw(i);
}

    *** Sparta internal interviews 'Quality Gates'
    	==> write a for loop on the WALL 
    	==> eg write out Fizz-Buzz code on the wall