# Create Azure Subscription - Enterprise Agreement



You will need a service principal with owner permission on the billing part of the enrollment. This can only be done with an account which has these permissions. 



1. Create service principal

2. Get service principal ID

```powershell
Get-AzServicePrincipal
```

3. Get EnrollmentAccountObjectID

```powershell
Get-AzEnrollmentAccount
```

4. Grant Access to Service Principal

```powershell
New-AzRoleAssignment -RoleDefinitionName Owner -ObjectId <userObjectId> -Scope /providers/Microsoft.Billing/enrollmentAccounts/<enrollmentAccountObjectId>
```



Request for Enterprise Agreement

```powershell
$request = @"
{
  "displayName": "JMB-IT-AVIATRIXPOC",
  "offerType": "MS-AZR-0017P",
  "owners": [
    {
      "objectId": "$OBJECTID"
    }
  ]
}
"@
```



MS-AZR-0017P = Offertype for "standard" Enterprise agreement sybscription







More information:

[https://docs.microsoft.com/nl-nl/azure/azure-resource-manager/management/grant-access-to-create-subscription?tabs=rest%2Crest-2]



[https://docs.microsoft.com/nl-nl/azure/azure-resource-manager/management/programmatically-create-subscription?tabs=rest]




