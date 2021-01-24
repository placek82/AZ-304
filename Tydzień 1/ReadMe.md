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

  - "polityka zabrania tworzenia serwerów Azure SQL, dostępnych publicznie":
```
{
  "properties": {
    "displayName": "Deny SQL Server with public access",
    "policyType": "Custom",
    "mode": "All",
    "metadata": {
      "category": "AZ-304",
      "createdBy": "e598a122-1aa1-4c5e-b422-4aad2b37b1e2",
      "createdOn": "2021-01-24T18:27:11.4528214Z",
      "updatedBy": null,
      "updatedOn": null
    },
    "parameters": {},
    "policyRule": {
      "if": {
        "allOf": [
          {
            "field": "type",
            "equals": "Microsoft.Sql/servers"
          },
          {
            "field": "Microsoft.Sql/servers/publicNetworkAccess",
            "equals": "Enabled"
          }
        ]
      },
      "then": {
        "effect": "deny"
      }
    }
  },
  "id": "/subscriptions/1195fe22-4e61-4a2a-9f5e-5d3b18f197fb/providers/Microsoft.Authorization/policyDefinitions/caf8836e-d9f6-4eb2-a56e-20bf6f0868d3",
  "type": "Microsoft.Authorization/policyDefinitions",
  "name": "caf8836e-d9f6-4eb2-a56e-20bf6f0868d3"
}
```

  - "polityka zabrania tworzenia zasobów, które nie mają Tag’u o nazwie Project":
```
{
  "properties": {
    "displayName": "Deny resources without Project tag",
    "policyType": "Custom",
    "mode": "Indexed",
    "metadata": {
      "createdBy": "e598a122-1aa1-4c5e-b422-4aad2b37b1e2",
      "createdOn": "2021-01-24T18:37:47.3644092Z",
      "updatedBy": "e598a122-1aa1-4c5e-b422-4aad2b37b1e2",
      "updatedOn": "2021-01-24T18:38:04.628413Z",
      "category": "AZ-304"
    },
    "parameters": {},
    "policyRule": {
      "if": {
        "field": "tags['Project']",
        "exists": "false"
      },
      "then": {
        "effect": "Deny"
      }
    }
  },
  "id": "/subscriptions/1195fe22-4e61-4a2a-9f5e-5d3b18f197fb/providers/Microsoft.Authorization/policyDefinitions/a4f1a07c-5d68-4b72-865c-4dec1a84c8d5",
  "type": "Microsoft.Authorization/policyDefinitions",
  "name": "a4f1a07c-5d68-4b72-865c-4dec1a84c8d5"
}
```

  - "polityka zabrania tworzenia zasobów, które nie mają Tag’u o nazwie Owner i którego zawartość nie zawiera maila np. w domenie chmurowisko.pl. Czyli tag Owner o wartości michal@chmurowisko.pl jest OK. ale tag o wartości michal@chmurowiskolab.com już nie":
```
{
  "properties": {
    "displayName": "Deny resources without Owner tag with value containing chmurowisko.pl",
    "policyType": "Custom",
    "mode": "All",
    "metadata": {
      "category": "AZ-304",
      "createdBy": "e598a122-1aa1-4c5e-b422-4aad2b37b1e2",
      "createdOn": "2021-01-24T18:45:19.6247055Z",
      "updatedBy": null,
      "updatedOn": null
    },
    "parameters": {},
    "policyRule": {
      "if": {
        "field": "tags['Owner']",
        "notLike": "*@chmurowisko.pl"
      },
      "then": {
        "effect": "deny"
      }
    }
  },
  "id": "/subscriptions/1195fe22-4e61-4a2a-9f5e-5d3b18f197fb/providers/Microsoft.Authorization/policyDefinitions/c365e4a0-2359-4920-95d8-9a43061511b0",
  "type": "Microsoft.Authorization/policyDefinitions",
  "name": "c365e4a0-2359-4920-95d8-9a43061511b0"
}
```

  - "polityka wymusza by każda stworzona maszyna była od razu podłączona do usługi Azure Log Analytics, które będzie parameterem polityk":
Po prostu [stąd](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Monitoring/LogAnalytics_OSImage_VMSS_Audit.json).

## Zadanie 2:



![](Img/traffic.png)
