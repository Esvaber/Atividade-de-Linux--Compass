# Atividade-de-Linux---Compass
Atividade da Bolsa de Estudos

Projeto para Bolsa de Estudos DevSecOps, da Compass Uol.

Aqui será construído a apresentação de todos os passos necessários para entregar os pedidos do time responsável pelos alunos da Bolsa.

Descrição das exigências:

Requisitos AWS:
<ul>
<li>Gerar uma chave pública para acesso ao ambiente;</li>
<li>Criar 1 instância EC2 com o sistema operacional Amazon Linux 2 (Família t3.small, 16 GB SSD);</li>
<li>Gerar 1 elastic IP e anexar à instância EC2;</li>
<li>Liberar as portas de comunicação para acesso público: (22/TCP, 111/TCP e UDP, 2049/TCP/UDP, 80/TCP, 443/TCP).</li>
</ul>

Requisitos no linux:
Configurar o NFS entregue;
Criar um diretorio dentro do filesystem do NFS com seu nome;
Subir um apache no servidor - o apache deve estar online e rodando;
Criar um script que valide se o serviço esta online e envie o resultado da
validação para o seu diretorio no nfs;
O script deve conter - Data HORA + nome do serviço + Status + mensagem personalizada de ONLINE ou offline;
O script deve gerar 2 arquivos de saida: 1 para o serviço online e 1 para o serviço OFFLINE;
Preparar a execução automatizada do script a cada 5 minutos.
Fazer o versionamento da atividade;
Fazer a documentação explicando o processo de instalação do Linux.

***Importante: Desligue a máquina quando não for utilizar, será descontado
pontos de máquinas que permanecerem ligadas em períodos fora de uso.
Entrega do PPT dia 09/02/24 apresentação dia 12/02/24
Entrega do GITHUB dia 09/02/24 e apresentação dia 13/02/24
