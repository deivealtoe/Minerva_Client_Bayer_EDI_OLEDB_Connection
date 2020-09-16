## OLEDB Connection

### Instalei o pacote ODAC122011_x64 (Oracle Data Access Components) em um Windows Server 2012 R2

#### Pode ser efetuado o download no link: [ODAC122011_x64.rar](https://mega.nz/file/RDYUBSLZ#pwoL9DvZtz-VYZiU8x7tFNBQs1QPAq3z7jKSmktMCVU)

#### Durante a instalação, marquei apenas:

+ Oracle Data Provider for .NET
+ Oracle Providers for ASP.NET
+ Oracle Provider for OLE DB

#### Após a instalação do cliente oracle

Precisamos configurar o arquivo **TNSNAMES.ORA**.

Pode ser usado o arquivo gerado pelo Oracle Client, como também pode ser criado um novo.

Basta criar um arquivo chamado **"tnsnames.ora"**

#### Exemplo do conteúdo de um arquivo tnsnames.ora

```
oracle_xe =
   (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = 192.168.1.6)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = xe) 
    )
  )
```

#### Após a configuração do arquivo tnsnames.ora, precisamos criar um novo registro nas variáveis do ambiente

1. Abrir o explorador de arquivos
2. Clicar com o botão direito em **"Este Computador"** e ir em **"Propriedades"**
3. Clicar em **"Configurações avançadas do sistema"**
4. Clicar em **"Variáveis de Ambiente..."**
5. Fazer tanto em **"Variáveis de usuário para ..."** quanto em **"Variáveis do Sistema"**
    1. Clicar em **"Novo"**
    2. Nome da variável **obrigatório** ser = **TNS_ADMIN**
    3. Valor da variável **onde está o arquivo tnsnames.ora** = **C:\app\client\TI\product\12.2.0\client_1\Network\Admin**
    4. Clicar em **"Ok"**
6. Clicar em **"Ok"**

#### Agora o sistema operacional precisa ser reiniciado.

#### No programa "Minerva Client"

Para testes, basta colocar **"1"** no campo Código SAP e **"Teste Minerva"** no campo Razão Social

Na aba Busca de Dados é necessário selecionar o tipo de conexão **OLE DB Connection** e inserir a seguinte string de conexão

**Provider=OraOLEDB.Oracle;Data Source=oracle_xe;User Id=sankhya;Password=xxxxxxxx;**

+ Provider é o tipo de conexão
+ Source é o nome definido no arquivo **tnsnames.ora**, nesse caso é **"oracle_xe"**
+ User Id é o nome do usuário do BD/schema
+ Password é a senha do BD
