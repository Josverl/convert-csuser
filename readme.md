
# Convert-CSUserData

## SYNOPSIS
    Extract Skype contact information from a pool Export-CSUserData and transform it for per-user import 
## DESCRIPTION
    Steps : 
    1. Export-CSUserData  .\export\DocItemSet.xml
    2. .\Convert-CSUserData.ps1  -InputFile .\export\DocItemSet.xml -OutPutPath .\export\
    3. .\Invoke-SFBContacts.ps1 -task import -file 'c:\test\Joe@contoso.com.csv'
## EXAMPLE
    #On a Single user export 
    Export-CS??? .\export\Joe.User.xml

    #convert single user to CSV
    .\Convert-CSUserData.ps1  -InputFile .\export\Joe.User.xml -OutPutPath .\export\ 

    .\Invoke-SFBContacts.ps1 -task import -file 'c:\test\Joe@contoso.com.csv'

## EXAMPLE
    #On a Pool Export
    Export-CSUserData  .\export\DocItemSet.xml

    #convert to mutiple CSVs
    .\Convert-CSUserData.ps1  -InputFile .\export\DocItemSet.xml -OutPutPath .\export\ -Base64

    .\Invoke-SFBContacts.ps1 -task import -file 'c:\test\Joe@contoso.com.csv'
## Example 
    #Batch conversion 

    Foreach( $file in (dir .\Batch-05\*.xml) ) {
        .\Convert-CSUserData.ps1 -InputFile $file.FullName -OutputPath '.\Batch-05'
    }