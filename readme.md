
```
vault policy write sample-policy sample-policy.hcl

vault token create -policy=sample-policy

export NEW_TOKEN=*****************

VAULT_TOKEN=$NEW_TOKEN vault read secret/data/mypassword
```
