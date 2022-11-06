
## run vault server as standalone

### start vault server

```bash
vault server -dev

# After starting vault server, you need to keep Unseal Key and Root Token shown on console.

Unseal Key:
Root Token: 

```

### Access to Vault server

```bash
export VAULT_ADDR="http://127.0.0.1:8200"
vault login
```

### register data into Vault

```bash
# register data
vault kv put secret/mypassword password=testpass

# show keys of stored data
vault kv list secret/

# get the stored data
vault kv get secret/mypassword

```

### get data using API

```bash
curl -H "X-Vault-Token: $(vault print token)" http://127.0.0.1:8200/v1/secret/data/mypassword
```

### put data using API

```bash
curl \ 
	-H "X-Vault-Token: $(vault print token)" \ 
	-H "Content-Type: application/json" \
	-X PUT -d '{"data":{"password":"hogeapi"}}' \
	http://127.0.0.1:8200/v1/secret/data/mypassword
```

you can also access to Vault server from Browser

[http://127.0.0.1:8200/ui/vault/auth]()


## Policy

show policy list

```
vault list sys/policy
```

read policy

```
vault read sys/policy/default
```


my memo

```
vault policy write sample-policy sample-policy.hcl

vault token create -policy=sample-policy

export NEW_TOKEN=*****************

VAULT_TOKEN=$NEW_TOKEN vault read secret/data/mypassword
```
