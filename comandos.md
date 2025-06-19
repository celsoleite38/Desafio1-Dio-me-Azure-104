
 Comandos e Ações Executadas no Gerenciamento de VMs Azure
 Conexão via SSH (Linux)
```bash
ssh -i ~/.ssh/minha-chave.pem usuario@ip-da-vm


criação de Maquinas Virtuais(CLI)
az vm create \
  --resource-group MeuGrupoDeRecursos \
  --name minhaVM \
  --image UbuntuLTS \
  --admin-username usuario \
  --ssh-key-values ~/.ssh/id_rsa.pub

Adicionar uma regra ao NSG (Grupo de Segurança de Rede).
az network nsg rule create \
  --resource-group MeuGrupoDeRecursos \
  --nsg-name meuNSG \
  --name PermitirHTTP \
  --protocol tcp \
  --priority 1000 \
  --destination-port-range 80 \
  --access allow \
  --direction inbound



Autoescalonamento em um Scale Set
az monitor autoscale create \
  --resource-group MeuGrupoDeRecursos \
  --resource minhaScaleSet \
  --min-count 2 \
  --max-count 5 \
  --count 3

Backup de VM
az backup protection enable-for-vm \
  --resource-group MeuGrupoDeRecursos \
  --vault-name MeuBackupVault \
  --vm minhaVM \
  --policy-name DefaultPolicy
