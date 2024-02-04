## Configurar o NFS
<p>Com o devido acesso ao Console AWS, será necessário seguir as seguintes etapas:</p>
<ol>
  <li>Acessar, pelo console, o serviço EFS</li>
  <li>Clicar no botão <i>Criar Sistema de arquivos</i></li>
</ol>
A partir desses passos será aberta a janela para preenchimento de dados.
<ul>
  <li>Clicar no botão <i>Personalizar</i></li>
  <ul>
    <li>Nome: <ins>EFS-Projeto</ins></li>
    <li>Todas as opções foram mantidas e cliquei em <i>Próximo</i></li>
    <li>Redes: confirmei que estava usando meu grupo de segurança padrão</li>    
    <li><b>Importante:</b> fui até meu grupo de segurança e fiz a liberação da porta 2049 TCP/UDP</li>
    <li>Clicar em <i>Próximo</i></li>
  </ul>
  <li>Não fiz alterações nas políticas. Clique em <i>Próximo</i> e na próxima tela clique no botão <i>Criar</i></li>
</ul>
Após aguardar a criação do Sistema de arquivos, proceder da seguinte maneira:
<ul>
  <li>Selecionar o Sistema de Arquivos criado: <i>EFS-Projeto</i></li>
  <li>Clique no botão <i>Visualizar Detalhes</i></li>
  <li>Clique no botão <i>Anexar</i></li>
  <li>Com a opção <i>Montar via DNS</i> selecionada, copie a linha de comando referente a opção <i>Usando o assistente de montagem do EFS</i> </li>
</ul>
Usando uma máquina virtual Linux previamente criada, fiz o acesso à minha Instância criada anteriormente.
Ao concluir o acesso, os seguintes passos devem ser feitos:
<ul>
  <li>Instalar o programa <i>amazon-efs-utils</i></li>
  <code>sudo yum install amazon-efs-utils -y</code>
  <li>Crie um novo diretório</li>
  <code>mkdir <i>nome-da-pasta</i></code>
  <li>Após a criação do diretório, cole o comando copiado do console AWS</li>
  <code>sudo mount -t efs -o tls fs-xxxxxxxx:/ <i>nome-da-pasta</i></code>
  <li>Para garantir a montagem do EFS na inicialização, é necessário alterar o arquivo <i>/etc/fstab</i> e acrescentar a linha abaixo</li>
  <code>fs-xxxxxxxx:/ <i>caminho/para/nome-da-pasta</i> efs _netdev,noresvport,tls,iam 0 0</code>
</ul>

## Criar um diretório dentro do filesystem do NFS com meu nome
<ul>
  <li>Dentro da instância, dentro do diretório criado para o EFS, crie um novo diretório</li>
  <code>sudo mkdir <i>meu-nome</i></code>
  <li>Depois da montagem, para garantir o funcionamento, crie uma instância e repita o processo de configuração do NFS</li>
  <li>Se tudo estiver correto, será possível visualizar o diretório <i>meu-nome</i> em ambas instâncias</li>
</ul>

## Subir um apache no servidor
<ul>
  <li>Com acesso à instância, rode no terminal o seguinte comando</li>
  <code>sudo yum -y install httpd</code>
  <li>Após a instalação, faça a inicialização do serviço</li>
  <code>sudo service httpd start</code>
  <li>Para fazer com que o apache rode junto com o boot, digite o comando abaixo</li>
  <code>sudo systemctl enable httpd</code>
</ul>
Após a instalação é necessário a criação de um arquivo html para teste de acesso ao servidor Apache.
<ul>
  <li>Acesse o diretório /var/www/html</li>
  <li>Lá dentro crie um arquivo .html</li>
  <code>sudo vim <i>nome-do-arquivo</i>.html</code>
  <li>Dentro do arquivo coloque uma mensagem que possa ser lida no navegador</li>
  <li>Acesse o arquivo usando o navegador. No meu caso meu endereço é http://52.202.207.69/</li>
</ul>

## Criar um script que valide se o serviço esta online e envie o resultado da validação para o seu diretório no nfs
<p>Serão feitas as seguintes sub-tarefas da tarefa principal:</p>
<ul>
  <i><li>O script deve conter - Data HORA + nome do serviço + Status + mensagem personalizada de ONLINE ou offline</li></i>
  <i><li>O script deve gerar 2 arquivos de saida: 1 para o serviço online e 1 para o serviço OFFLINE</li></i>
</ul>

Após o acesso da instância criada para o projeto, fiz os seguintes procedimentos:
<ul>
  <li>Usando o usuário root, foi criado, no diretório <i>/home/ec2-user</i>, o arquivo <i>script.sh</i></li>
  <code>touch script.sh</code>
  <li>O arquivo foi modificado para permitir sua execução</li>
  <code>chmod +x script.sh</code>
  <li>A partir daí o código usado para o script segue</li>
  <pre>
    
    #!/bin/bash

    #Cria um variável com a data no formato dia_mês_ano hh:mm:ss, corrigido para o fuso horário da minha região
    data=$(TZ='America/Sao_Paulo' date "+%d_%b_%Y_%T")
    
    #Cria uma variável para o resultado e faz a verificação se o apache está ativo
    status=""
    
    if systemctl is-active "httpd" > /dev/null
    then
            status="ativo"
    else
            status="inativo"
    fi
    
    #Cria o arquivo que será salvo no NFS
    arquivo="/home/ec2-user/efs/esvaber/apache_${status}_${data}.txt"
    
    #Adiciona o resultado e o timestamp dentro do arquivo
    echo "$data" > "$arquivo"
    echo "O Apache está $status" >> "$arquivo"

  </pre>
</ul>

## Preparar a execução automatizada do script a cada 5 minutos

<p>Para automatizar o script usaremos o cronotab</p>
<ul>
  <li>Dentro da isntância, no terminal, usaremos o código</li>
  <code>crontab -e</code>
  <li>Dentro do editor que será aberto, usaremos a linha abaixo para programa sua execução a cada 5 minutos</li>
  <code>*/5 * * * * /path/to/your/script.sh</code>
</ul>
