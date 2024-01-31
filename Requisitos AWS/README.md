## Criação de chave pública
<p>A criação da chave pública necessita do acesso ao painel da AWS. Ao acessar o painel, segui as seguintes etapas:</p>
<ol>
  <li>Acesso ao serviço EC2</li>
  <li>Dentro do grupo <i>Rede e Segurança</i>, selecionei a opção <i>Pares de chaves</i></li>
  <li>Cliquei no botão <i>Cria par de chaves</i>, que me abre opções para criação da chave</li>
</ol>
Dentro das opções de criação, preenchi da seguinte maneira:
<ul>
  <li>Nome: <b><i>MinhaChave</i></b></li>
  <li>Tipo de par de chaves: <b><i>RSA</i></b></li>
  <li>Formato de arquivo de chave privada: <b><i>.pem</i></b></li>
</ul>
<p>Após clicar em <i>Criar par de chaves</i>, é necessário salvar o arquivo gerado para futuro acesso.</p>

## Criação de instância EC2
<p>Com o acesso ao console, fiz os seguintes procedimentos:</p>
<ol>
  <li>Acesso ao serviço EC2</li>
  <li>Dentro do grupo <i>Instâncias</i>, opção <i>Instâncias</i></li>
  <li>Cliquei no botão <i>Executar Instâncias</i>, que me conduz para a tela de criação</li>
</ol>
As opções de preenchimento seguem:
<ul>
  <li>Devido às condições do acesso ao console, foi necessário clicar na opção <i>Adicionar mais tags</i> e incluir as tags abaixo</li>
  <ul>
    <li>Chave: Name / Valor: Projeto Linux / Tipos de Recurso: Instâncias e Volumes</li>
    <li>Chave: CostCenter / Valor: ######## / Tipos de Recurso: Instâncias e Volumes</li>
    <li>Chave: Project / Valor: ######### / Tipos de Recurso: Instâncias e Volumes</li>
  </ul>
  <li>Application and OS Images: Fiz a seleção da Imagem Amazon Linux 2 AMI (HVM), 64 bits (x86).</li>
  <li>Tipo de instância: selecionei a opção t3.small</li>
  <li>Par de chaves: selecionei minha chave criada anteriormente: <b>MinhaChave</b></li>
  <li>Configurações de rede: fiz as seguintes alterações</li>
  <ul>
    <li>VPC: fiz a criação de uma nova VPC chamada <b>projeto-linux</b></li>
    <li>Sub-rede: selecionei a sub-rede <b>publica01-projeto</b>, criada juntamento com a VPC</li>
    <li>Atribuir IP público automaticamente: Habilitar</li>
    <li>Firewall (grupos de segurança): Criar grupo de segurança</li>
    <ul>
      <li>Nome do grupo de segurança: SG-projeto</li>
      <li>Descrição: SG-projeto</li>
      <li>Regras do grupo de segurança de entrada: nenhuma regra adicionada</li>
    </ul>
  </ul>
  <li>Configurar armazenamento: 1 disco de 16 GB, gp2 </li>
</ul>
Após as configurações, cliquei no botão <i>Executar Instância</i> e aguardei a criação da mesma.

## Gerar elastic IP e anexar à instância EC2

## Liberar as portas de comunicação para acesso público
