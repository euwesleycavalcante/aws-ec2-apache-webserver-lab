
# Documentação Técnica | Amazon EC2 e Apache

> Laboratório guiado de provisionamento, configuração,
> monitoramento e redimensionamento de uma instância
> Amazon EC2 utilizada como servidor web.

[← Voltar para o guia de iniciantes](guia-iniciantes.md)

## 1. Visão geral

Este projeto documenta a implementação de um servidor
web Apache em uma instância Amazon EC2, utilizando
recursos de infraestrutura da AWS.

O laboratório contempla:

- Provisionamento de instância EC2
- Configuração de rede e Security Groups
- Automatização da instalação do Apache via User Data
- Monitoramento com Amazon CloudWatch
- Redimensionamento de instância e armazenamento EBS
- Validação da proteção contra encerramento

## 2. Arquitetura da solução

Componentes utilizados:

| Componente | Configuração |
|------------|--------------|
| Computação | Amazon EC2 |
| Sistema operacional | Amazon Linux 2023 |
| Instância inicial | t3.micro |
| Instância redimensionada | t3.small |
| Servidor web | Apache HTTP Server |
| Rede | Lab VPC |
| Segurança | Security Group |
| Protocolo de acesso | HTTP / TCP 80 |
| Armazenamento | Amazon EBS, 8 GiB → 10 GiB |
| Monitoramento | Amazon CloudWatch |

## 3. Provisionamento

A instância foi configurada com proteção contra
encerramento habilitada e sem par de chaves SSH,
conforme os requisitos do laboratório.

A instalação do servidor web foi automatizada
por meio do User Data.

## 4. Script de inicialização

O script utilizado executa a instalação e ativação
do Apache e cria uma página HTML básica.

O código será mantido separadamente no arquivo
`user-data.sh`, na raiz do repositório.

## 5. Configuração de segurança

Inicialmente, o Security Group não possuía regras
de entrada, impedindo o acesso HTTP externo.

Foi adicionada uma regra com os parâmetros:

- Tipo: HTTP
- Protocolo: TCP
- Porta: 80
- Origem: 0.0.0.0/0

A configuração demonstra o controle de acesso
à instância por meio do Security Group.

## 6. Monitoramento

Foram exploradas as verificações de integridade
da instância e as métricas disponíveis na
guia de monitoramento do Amazon EC2.

Também foi utilizada a funcionalidade de captura
de tela da instância para observação do console.

## 7. Redimensionamento

O laboratório incluiu:

- Interrupção da instância EC2
- Alteração do tipo t3.micro para t3.small
- Expansão do volume EBS de 8 GiB para 10 GiB
- Reinicialização da instância

## 8. Proteção contra encerramento

Foi realizado um teste de encerramento com a
proteção habilitada.

Após a validação, a proteção foi desabilitada
e o encerramento da instância foi solicitado.

## 9. Limitações e considerações

Este projeto corresponde a um laboratório
educacional guiado realizado duarante o curso AWS RE/Start da Escola da Nuvem e ministrado pelo professor Raphael Olsen, e não a uma implantação
de produção.

A exposição da porta HTTP 80 para qualquer IPv4
foi utilizada exclusivamente no contexto didático.

O ambiente não inclui HTTPS, balanceamento de carga,
alta disponibilidade ou infraestrutura como código.

## 10. Próximas melhorias

- Adicionar diagrama de arquitetura
- Incluir evidências visuais da execução
- Documentar testes e resultados
- Explorar alternativas de segurança para produção
- Evoluir a infraestrutura com automação
