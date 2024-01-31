<h1> Requisitos AWS </h1>

<h3> Lista de requisitos </h3>
<ul>
  <li>Gerar uma chave pública para acesso ao ambiente;</li></a>
  <li>Criar 1 instância EC2 com o sistema operacional Amazon Linux 2 (Família t3.small, 16 GB SSD);</li></a>
  <li>Gerar 1 elastic IP e anexar à instância EC2;</li>
  <li>Liberar as portas de comunicação para acesso público: (22/TCP, 111/TCP e UDP, 2049/TCP/UDP, 80/TCP, 443/TCP).</li>
</ul>

## Gerar uma chave pública para acesso ao ambiente
<p>A criação da chave pública necessita do acesso ao painel da AWS. Ao acessar o painel, seguimos as seguintes etapas:</p>
<ul>
  <li>Acesso ao serviço EC2</li>
  <li>Dentro de <i>Rede e Segurança</i>, selecionar a opção <i>Pares de chaves</i></li>
  <li>Clicar no botão <i>Cria par de chaves</i></li>
</ul>
Dentro das opções de criação, iremos definir da seguinte maneira:
<ul>
  <li>Nome: <b><i>MinhaChave</i></b></li>
  <li>Tipo de par de chaves: <b><i>RSA</i></b></li>
  <li>Formato de arquivo de chave privada: <b><i>.pem</i></b></li>
</ul>
<p>Após clicar em <i>Criar par de chaves</i>, é necessário salvar o arquivo gerado para futuro acesso.</p>

## Criar 1 instância EC2 com o sistema operacional Amazon Linux 2

