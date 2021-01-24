### TYDZIEŃ1
## Zadanie 1:
    - "politka zabrania stworznia konta typu Azure Storage, które umożliwia dostępu z tzw. Public Endpoints":
```
{
  "properties": {
    "displayName": "Deny storage with public endpoint",
    "policyType": "Custom",
    "mode": "All",
    "description": "Policy denies creating storage accounts with public endpoints",
    "metadata": {
      "category": "AZ-304",
      "createdBy": "e598a122-1aa1-4c5e-b422-4aad2b37b1e2",
      "createdOn": "2021-01-24T17:48:18.8020639Z",
      "updatedBy": "e598a122-1aa1-4c5e-b422-4aad2b37b1e2",
      "updatedOn": "2021-01-24T17:51:09.4876777Z"
    },
    "parameters": {},
    "policyRule": {
      "if": {
        "allOf": [
          {
            "field": "type",
            "equals": "Microsoft.Storage/storageAccounts"
          },
          {
            "field": "Microsoft.Storage/storageAccounts/networkAcls.defaultAction",
            "equals": "Allow"
          }
        ]
      },
      "then": {
        "effect": "deny"
      }
    }
  },
  "id": "/subscriptions/1195fe22-4e61-4a2a-9f5e-5d3b18f197fb/providers/Microsoft.Authorization/policyDefinitions/818713c5-2521-4bfe-b8e8-b57d9ef7b8d3",
  "type": "Microsoft.Authorization/policyDefinitions",
  "name": "818713c5-2521-4bfe-b8e8-b57d9ef7b8d3"
}
```

## Zadanie 2:



![](Img/traffic.png)
