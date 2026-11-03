# Política de Privacidade da Arielzinha

**Última atualização:** 3 de novembro de 2026

## Resumo

Esta política explica quais informações a Arielzinha trata, para que são utilizadas e quais limitações existem nos controles de retenção e exclusão.

- **Identificadores:** IDs de usuário, servidor e canal do Discord são utilizados para comandos, configurações e permissões.
- **Dados persistidos:** configurações de servidores, preferências de usuários, favoritos, integrações e dados de vinculação ao Last.fm podem ser armazenados.
- **Comandos e mensagens:** o bot recebe mensagens dos servidores para identificar comandos e pedidos por menção. O conteúdo não é descrito aqui como sendo arquivado integralmente; entretanto, o registro opcional de comandos pode guardar o texto ou as opções executadas.
- **Terceiros:** a operação pode envolver Discord, Last.fm, provedores de música, hospedagem e infraestrutura.
- **Exclusão:** não há, no código atual, um mecanismo público de autoatendimento que apague todos os dados. Remover o bot de um servidor não apaga automaticamente os registros já persistidos.

## 1. Introdução

Esta Política de Privacidade se aplica ao bot de música **Arielzinha** para Discord. Ela descreve o tratamento de dados realizado pela implementação disponível no repositório [DEVenur/Arielzinha](https://github.com/DEVenur/Arielzinha).

O tratamento efetivo pode variar conforme a configuração da instância, especialmente quanto ao banco de dados, aos registros de comandos, aos logs e às integrações habilitadas.

## 2. Informações tratadas

### 2.1. Identificadores e dados de contexto do Discord

Durante a operação, o bot utiliza identificadores como:

- ID do usuário que executa um comando;
- ID do servidor (guild) e do canal;
- informações de contexto necessárias para verificar permissões, cargos, canais e presença em canais de voz.

O bot também consulta, em tempo real, membros e estados de voz para executar funcionalidades do player. A implementação utiliza essas informações durante a operação; esta política não afirma que todo o histórico de presença seja armazenado.

### 2.2. Dados persistidos de usuários

A implementação possui registros associados ao ID do usuário que podem incluir:

- prefixo personalizado;
- links favoritos;
- dados de integração;
- token ou credenciais de integração, quando utilizados pelos recursos correspondentes;
- histórico ou informações recentes de faixas;
- nome de usuário, chave de sessão do Last.fm e preferência de scrobble;
- dados auxiliares necessários às funcionalidades do bot.

A chave de sessão do Last.fm é uma credencial de acesso à conta vinculada e deve ser tratada como informação sensível de autenticação.

### 2.3. Dados persistidos de servidores

Os registros associados aos servidores podem incluir:

- prefixo do servidor;
- configurações do player e dos canais de controle;
- skins e personalizações;
- cargos e configurações relacionadas ao uso do player;
- status de canal de voz e convites de escuta conjunta;
- outras preferências necessárias às funcionalidades habilitadas.

### 2.4. Filas, faixas e dados auxiliares

O bot pode salvar filas de reprodução associadas ao usuário, incluindo metadados das faixas, data de criação e ID do servidor. A implementação grava essas filas em arquivos locais.

O recurso de scrobble também mantém registros locais auxiliares de faixas que não puderam ser identificadas ou enviadas ao Last.fm. Há ainda caches locais de metadados e resultados de consultas. Esses arquivos não devem ser confundidos com um histórico completo de todas as mensagens ou de toda a atividade do usuário.

### 2.5. Mensagens, comandos e logs

O bot recebe mensagens dos servidores para reconhecer comandos com prefixo, menções e pedidos de música. Isso não significa que todas as mensagens sejam gravadas em um banco de dados.

Há, porém, opções de diagnóstico:

- **COMMAND_LOG:** quando ativada, registra comandos executados, identificadores do usuário e servidor e, para comandos de prefixo, o conteúdo da mensagem. Para comandos de barra, registra o nome do comando e as opções preenchidas. Essa opção vem desativada por padrão no arquivo de configuração de exemplo.
- **ENABLE_LOGGER:** quando ativada, grava logs técnicos em `.logs/disnake.log`. O conteúdo depende dos eventos e mensagens emitidos pelas bibliotecas e pelo próprio bot. Essa opção também vem desativada por padrão no arquivo de configuração de exemplo.
- **Saída do processo:** mensagens de diagnóstico e erros podem ser enviadas à saída padrão. A plataforma de hospedagem pode capturar e reter essa saída conforme suas próprias configurações.

Não existe, no código analisado, um prazo universal que garanta a eliminação automática de todos esses registros.

## 3. Finalidades do tratamento

Os dados são utilizados para:

- executar comandos e controlar a reprodução de música;
- aplicar configurações, permissões e preferências de usuários e servidores;
- manter favoritos, filas salvas e recursos de personalização;
- vincular contas Last.fm e registrar faixas quando o usuário habilita o scrobble;
- manter integrações e recursos associados;
- diagnosticar erros, monitorar o funcionamento e investigar abusos, quando os registros correspondentes estiverem habilitados.

## 4. Serviços de terceiros e compartilhamento

A utilização do bot pode envolver os seguintes serviços:

- **Discord:** plataforma na qual o bot recebe comandos, identificadores, contexto de servidor e eventos necessários às funcionalidades.
- **Last.fm:** quando a integração é configurada, o bot utiliza a API do Last.fm para autenticar a conta, consultar informações e enviar dados de faixas para now playing e scrobble. Isso pode incluir nome do artista, título, álbum, duração e chave de sessão.
- **Serviços de música:** conforme a fonte e a funcionalidade utilizada, consultas e metadados podem ser processados por serviços como Spotify, Deezer e servidores Lavalink configurados na instância.
- **Hospedagem e banco de dados:** os dados podem ser armazenados na infraestrutura local do operador ou em MongoDB, conforme a configuração da instância. O provedor de hospedagem e o provedor de banco de dados podem ter acesso técnico aos dados sob sua infraestrutura.

**Observação técnica sobre Last.fm:** na versão do código consultada, as requisições à API do Last.fm utilizam o endereço HTTP `http://ws.audioscrobbler.com/2.0/`, e não HTTPS. Isso significa que a comunicação dessa integração não oferece criptografia de transporte por HTTPS nessa implementação. O operador deve considerar esse risco antes de habilitar a integração.

Não vendemos dados pessoais. O operador da instância deve avaliar os serviços de terceiros efetivamente habilitados e as respectivas políticas e condições.

## 5. Armazenamento e retenção

A implementação suporta armazenamento em TinyMongo local ou MongoDB, conforme a configuração. Além disso, determinados dados auxiliares — incluindo dados de scrobble, caches e filas salvas — são gravados em arquivos locais.

A duração do armazenamento depende da configuração, da infraestrutura, das rotinas de manutenção e das ações do operador. O código consultado não estabelece um prazo único de retenção nem garante a exclusão automática de todos os dados após determinado período.

Remover o bot de um servidor interrompe sua operação naquele servidor, mas não remove automaticamente os registros existentes no banco de dados, arquivos locais, backups ou logs da hospedagem.

## 6. Segurança

O operador deve proteger os arquivos de banco de dados, backups, variáveis de ambiente, tokens e chaves de sessão, restringindo o acesso às pessoas autorizadas. A segurança também depende da configuração e das práticas do provedor de hospedagem e do banco de dados.

Não é correto interpretar esta política como uma garantia de criptografia em repouso, criptografia em trânsito em todos os serviços ou segurança absoluta. Em particular, a integração Last.fm da versão consultada utiliza HTTP, conforme descrito acima.

## 7. Solicitações de acesso, correção ou exclusão

O código atual não disponibiliza um comando público que permita ao usuário consultar, exportar ou apagar integralmente todos os dados associados à sua conta.

Para solicitar acesso, correção ou exclusão, entre em contato com o operador pelo [servidor oficial de suporte no Discord](https://dcserver.link/brasilpokedrink). Inclua informações suficientes para localizar os registros, sem enviar senhas, tokens ou chaves de sessão.

A remoção de dados pode exigir ações no banco de dados e nos arquivos da instância. A exclusão de backups e registros mantidos pelo provedor de hospedagem depende também das políticas e dos recursos desse provedor. Não há um prazo automático de conclusão implementado pelo bot.

## 8. Privacidade de menores

O uso da Arielzinha deve respeitar os requisitos de idade aplicáveis ao Discord e à legislação da região do usuário. O operador não deve permitir o uso do serviço em desacordo com esses requisitos.

## 9. Alterações nesta política

Esta política pode ser atualizada para refletir mudanças no código, nas configurações ou nos serviços utilizados. A versão vigente será publicada neste repositório.

## 10. Contato

Para dúvidas ou solicitações relacionadas aos dados tratados pela instância Arielzinha, utilize o [servidor oficial de suporte no Discord](https://dcserver.link/brasilpokedrink).
