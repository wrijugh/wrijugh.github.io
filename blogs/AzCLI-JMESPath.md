Azure CLI retuns JSON output bydefault. To find the right information we use JMESPath to query the JSON string. Azure CLI Allows you to pass the value in ```--query``` parameter. 

Before we jump to the Azure CLI we can dive into the basics of JMESPath to find a bit more details.

Let's assume that we have the below sample JSON
```json
{
    "employees":
    [
        {
            "name": "Wriju", 
            "email": "wriju@contoso.com",
            "city": "Bangalore"        
        },
        {
            "name": "Wrishika", 
            "sal":
            {
                "jan":"100",
                "feb":"200"
            }
        },
        {
            "name": "Wrishika", 
            "email": "wrishika@contoso.com",
            "city": "Mysore",
            "sal":
            {
                "jan":"100",
                "feb":"200"
            }
        },
        {
            "name": "Writam", 
            "email": "writam@contoso.com",
            "city": "Siliguri"
        }
    ]
}
```
To get all the values we can write 
```employees``` then it will return all the values