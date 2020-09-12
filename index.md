# Azure CLI filter the JSON Output with JMESPath
Azure CLI retuns JSON output by default. To find the right information we use JMESPath to query the JSON string. Azure CLI Allows you to pass the value in ```--query``` parameter. 

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
```employees``` then it will return all the values. If you want to view the values only from field ```name``` then you can use 
```
employee[*].name
```
This would result in as 
```json
[
  "Wriju",
  "Wrishika",
  "Wrishika",
  "Writam"
]
```
Now imagine you want to read the **jan** value from **sal** property then you would write
```
employee[1].sal.jan
```
so on and so forth. 

In **Azure CLI** we can also use it filter the output result. If I want to get the **admin user name** of a VM that information is stored in 
```json
"osProfile": {
      "adminPassword": null,
      "adminUsername": "wriju",
      "allowExtensionOperations": true,
      "computerName": "wm-Ubuntu18",
      ...
```
So we can use ```osProfile.adminUsername```

The final **Azure CLI** would look like,

```bash
az vm show -g rg-vm -n wm-Ubuntu18 --query "osProfile.adminUsername"
```
