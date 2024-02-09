# Atividade-de-Linux--Compass
Projeto para Bolsa de Estudos DevSecOps, da Compass Uol.

Aqui está todo o escopo do projeto. Ele está dividido em duas partes e seus tópicos podem ser acessados abaixo.

<h1><b>Requisitos AWS</b></h1>

<ul>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20AWS/index.md#cria%C3%A7%C3%A3o-de-chave-p%C3%BAblica"><li>Gerar uma chave pública para acesso ao ambiente</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20AWS/index.md#cria%C3%A7%C3%A3o-de-inst%C3%A2ncia-ec2"><li>Criar 1 instância EC2 com o sistema operacional Amazon Linux 2 (Família t3.small, 16 GB SSD)</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20AWS/index.md#gerar-elastic-ip-e-anexar-%C3%A0-inst%C3%A2ncia-ec2"><li>Gerar 1 elastic IP e anexar à instância EC2</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20AWS/index.md#liberar-as-portas-de-comunica%C3%A7%C3%A3o-para-acesso-p%C3%BAblico"><li>Liberar as portas de comunicação para acesso público: (22/TCP, 111/TCP e UDP, 2049/TCP/UDP, 80/TCP, 443/TCP)</li></a>
</ul>



<h1><b>Requisitos Linux</b></h1>
<ul>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20Linux/index.md#configurar-o-nfs><li>Configurar o NFS entregue</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20Linux/index.md#criar-um-diret%C3%B3rio-dentro-do-filesystem-do-nfs-com-meu-nome"><li>Criar um diretorio dentro do filesystem do NFS com seu nome</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20Linux/index.md#subir-um-apache-no-servidor"><li>Subir um apache no servidor - o apache deve estar online e rodando</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20Linux/index.md#criar-um-script-que-valide-se-o-servi%C3%A7o-esta-online-e-envie-o-resultado-da-valida%C3%A7%C3%A3o-para-o-seu-diret%C3%B3rio-no-nfs"><li>Criar um script que valide se o serviço esta online e envie o resultado da validação para o seu diretorio no nfs</li></a>
  <ul>
    <li>O script deve conter - Data HORA + nome do serviço + Status + mensagem personalizada de ONLINE ou offline</li>
    <li>O script deve gerar 2 arquivos de saida: 1 para o serviço online e 1 para o serviço OFFLINE</li>
  </ul>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/blob/main/Requisitos%20Linux/index.md#preparar-a-execu%C3%A7%C3%A3o-automatizada-do-script-a-cada-5-minutos"><li>Preparar a execução automatizada do script a cada 5 minutos</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/releases"><li>Fazer o versionamento da atividade</li></a>
  <a href="https://github.com/Esvaber/Atividade-de-Linux--Compass/tree/main/Requisitos%20Linux"><li>Fazer a documentação explicando o processo de instalação do Linux</li></a>
</ul>

