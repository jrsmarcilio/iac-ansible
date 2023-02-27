# Mãos na massa: Começando com o Ansible e EC2

1. Crie um diretório para o projeto e entre nele:
  
```bash
mkdir myproject
cd myproject
```

2. Crie uma instância EC2 na AWS e faça o download da chave de acesso. Salve a chave de acesso no diretório do projeto.

3. Crie um arquivo chamado `hosts` e adicione o endereço IP da instância EC2 criada no passo anterior. Exemplo:
  
```bash
[wordpress]
ec2-ip-address

[wordpress:vars]
ansible_user=ec2-user
ansible_ssh_private_key_file=ec2-key.pem

ansible_python_interpreter=/usr/bin/python3.7
```

4. Rode o comando Ansible abaixo para ter um simples hello world:

```bash
ansible wordpress -i hosts -m shell -a 'echo Hello World'
```

5. Para ter uma saída com detalhes da execução do comando, adicione o parâmetro `-vvv`:

```bash
ansible wordpress -i hosts -m shell -a 'echo Hello World'
```

6. Para a instalação do Apache e do PHP, execute o playbook chamado `provisioning.yml`:

```bash
ansible-playbook provisioning.yml -i hosts
```
