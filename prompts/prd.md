# Prompt PRD 

A seguir foi elebarado instruções usadas auxiliar na criação do PRD de acordo com o contexto da aplicação inserida. Foi utilizado o assistente de IA conversacional Grok como principal ferrameta de geração de texto.

## Instrução no projeto

```text
Com base no contexto e escopo do projeto fornecido, gere um PRD completo contendo:

- Mini-mundo;
- Requisitos funcionais;
- Requisitos não funcionais;
- Regras de negócio;
- Diagrama de caso de uso (formato textual estruturado, estilo UML);
- Modelo lógico de banco de dados (tabelas, atributos, tipos e relacionamentos);
- Cenários de testes de software;
- Possível fluxo de telas.

Cada requisito funcional deve ter:

- ID (Ex: RF001 - SIGA ESSE PADRÃO);
- Caso de Uso (nome objetivo da funcionalidade que representa o comportamento esperado do sistema);
- Descrição (explica de forma clara o que o sistema deve fazer e qual o objetivo da funcionalidade, geralmente com o foco no usuário final e no propósito do requisito);
- Atores (papeis de usuários ou sistemas externos que interagem com a funcionalidade; relacionado a uma funcionalidade específica);
- Requisito de Dependência (outros requisitos funcionais que precisam estar presentes ou operacionais para que este requisito funcione corretamente - Diga somente o ID);
- Dados de Entrada (Nome, Tipo de Dado, Valor Obrigatŕio S/N, Propriedade/Regra) -> como se fosse o body de um endpoit ou parâmetro obrigatório na URL -> Em tabela;
- Dados de Saída (Nome, Tipo de Dado, Valor Obrigatŕio S/N, Propriedade/Regra) -> como se fosse o response de um endpoint -> Em tabela;

Cada requisito não funcional deve ter:

- ID (Ex: RNF001 - SIGA ESSE PADRÃO);
- Descrição (explica a qualidade que o sistema deve cumprir, sem estar diretamente relacionado a uma funcionalidade específica.);
- Categoria (Segurança: proteção de dados sensíveis; Capacidade: armazenamento e processamento necessários; Compatibilidade: suporte a sistemas e hardware; Disponibilidade: estabilidade e tempo online; Manutenibilidade: facilidade de suporte técnico; Escalabilidade: crescimento sem perda de desempenho; Usabilidade: facilidade e experiência do usuário; Desempenho: tempo de resposta adequado; Conformidade: atendimento a normas legais; Ambiental: adaptação ao ambiente físico).

Cada regra de negócio deve ter:

- ID (Ex: RN001 - SIGA ESSE PADRÃO);
- Descrição (explica a restrição ou regra que o sistema deve cumprir);
- Dependência (outra regra de negócio que precisa estar presentes ou operacionais para que esta regra funcione corretamente); 

Cada diagrama deve:

- ser representados em formato textual estruturado (ex: estilo UML ou Mermaid)
- Não utilizar imagens
- Devem ser coerentes com os requisitos funcionais

O modelo de banco de dados deve conter:

- Tabelas com: nome, atributos, tipos de dados, regras se são únicos ou não, regras se podem ser nulas ou não, chaves primárias e chaves estrangeiras;
- Relacionamentos explícitos com cardinalidade, exemplo: [Tabela X] (0, n) ... (1, 1) [Tabela Y];
- Deve refletir os requisitos funcionais.


Cada cenário de teste de software, deve ter um caso de sucesso e vários casos de falha cobrindo validações, regras de negócio, fluxos alternativos e casos extremos. Gere em formato de tabelas. Sendo assim, para cada requisito funcional:

- Criar pelo menos: 1 cenário de sucesso e 3 cenários de falha;
- Ter formato em tabela com: ID do teste, requisito relacionado, descrição, entrada, Resultado esperado;
- As tabelas tem que está em formato.md;
- Todos os cenários de teste devem cobrir validações de campos, regras de negócio e casos extremos (edge cases), quando aplicável.


Regras gerais:

- As respostas devem ser em formato markdown;
- Não crie imagens quando for criar os diagramas ou fluxos de telas, apenas textos, que organizados, ilustram o diagrama;
- Garantir consistência entre requisitos funcionais, requisitos não funcionais, regra de negócios, banco de dados e cenários de testes;
- Todos os IDs (RF, RNF, RN e testes) devem ser únicos e não podem se repetir;
- Se o contexto ou escopo do projeto estiver incompleto ou ambíguo, faça perguntas antes de gerar o PRD;
- Não inventar funcionalidades fora do escopo fornecido;
- REFORÇO! NÃO CRIE OU MANDE UM ARQUIVO, MAS SIM RESPOSTAS COM FORMATO *MARKDOWN*;
- ME MANDE EM FORMATO .MD;
- AS TABELAS, DIAGRAMAS E IMAGENS DEVE SEGUIR O FORMATO .MD.
```

## Contexto Incluso (o que foi mandado no chat)

```text
### Contexto
 
O Âmago é uma rede social criada para compartilhar memórias de momentos íntimos já vividos, despertando aquele gostinho do passado, profundo e marcante, que merece ser revivido mais uma vez.
 
O projeto, antes chamado de *Âmago*, foi refatorado para que o aplicativo não seja apenas uma rede social de criação de posts, mas uma plataforma que traga mais significado aos usuários, priorizando práticas de gestão de projeto, qualidade de software, uso de IA e clareza arquitetural.
 
### Escopo
 
#### Iteração 000 (Piloto - MVP técnico)
 
A Iteração Piloto corresponde à criação do primeiro Produto Mínimo Viável (Minimum Viable Product - MVP), desenvolvido com foco na validação técnica da aplicação. Nesta fase, o sistema ainda não possuía um direcionamento claro como produto, sendo estruturado principalmente como uma base funcional para gerenciamento de usuários e posts.
 
Além disso, nesta fase, não foi realizada a implantação em ambiente de nuvem nem a publicação em lojas de aplicativos, mantendo o projeto restrito a um ambiente local e controlado para fins de desenvolvimento e validação.
 
Dessa forma, não foram implementadas funcionalidades avançadas de interação social, como visualização de perfis de outros usuários, detalhamento de posts individuais, sistema de seguidores, curtidas, comentários, compartilhamento de conteúdo, stories e sistema de chat interativo entre usuários.
 
Assim, as funcionalidades contempladas nesta iteração incluem:
 

- Registro, login, logout, atualização, detalhamento e persistência de dados de usuários;
- Criação de posts com suporte a upload de arquivos e captura de fotos pela câmera do dispositivo;
- Edição e remoção de posts;
- Filtragem de posts por tipo de conteúdo (IMAGE, VIDEO e TEXT);
- Listagem de todos os posts do usuário.
 
#### Iteração I
 
A Iteração I representa a evolução do MVP técnico para uma versão mais orientada a produto, com foco na melhoria da experiência do usuário, qualidade de software e maturidade no processo de desenvolvimento.
 
Além disso, nesta iteração, ainda não foi realizada a implantação em ambiente de nuvem nem a publicação em lojas de aplicativos, mantendo o foco no desenvolvimento, testes e evolução do sistema em ambiente controlado.
 
Apesar dos avanços, ainda não foram implementadas funcionalidades mais avançadas de rede social, como sistema completo de seguidores, curtidas em tempo real, comentários em posts, compartilhamento de conteúdo entre usuários, stories e sistema de chat interativo entre usuários.
 
Dessa forma, as funcionalidades e melhorias contempladas nesta iteração foram:
 
- Uso de IA para automatizar a geração de código com supervisão humana, aumentando a produtividade sem comprometer a qualidade;
- Definição e especificação do PRD (Product Requirements Document), promovendo maior clareza de requisitos e organização do projeto;
- Adoção contínua de testes (unitários e de integração), priorizando a qualidade e confiabilidade do software;
- Modificação e refinamento do layout, melhorando a experiência do usuário (UX) e a interface visual (UI);
- Correção de erros relacionados à atualização de arquivos em posts;
- Implementação da visualização detalhada de posts individuais;
- Implementação da visualização de perfis de outros usuários;
- Remoção completa da conta de usuário;
- Remoção de arquivos de posts e de usuário;
- Otimização da performance geral do aplicativo.

### Dados

[User] {id (pk uuid not null), name(varchar 225 not null), e-mail(varchar 255 not null), password(varchar 10 not null), bio(text null), image(text null), created_at(timestamp not null), updated_at(timestamp null)}
 
(0..n) --- (1..1)
[Post] {id (pk uuid not null), id_user(fk User.id not null), title(varchar 255 not null), description(text not null), post_type(enum 'TEXT', 'IMAGE', 'VIDEO' default 'TEXT'), file (text null), created_at(timestamp not null), updated_at(timestamp null)} 
 
### Regras:
 
- Um usuário pode ter nenhum ou vários posts, cada post deve pertencer a um e somente a um usuário.
- A senha deve ter ao menos 6 caracteres e no máximo 10 caracteres;
- O e-mail de usuário deve ser único para cada usuário e com formato de e-mail;
- Cada post pode ser atualizado com um arquivo diferente. Exemplo: Se um post for só texto e atualiza colocando uma imagem ou vídeo; Se o post tem uma imagem ou vídeo, o usuário pode remove-la deixando só o texto, fazendo com que a antiga imagem ou video seja deletada do banco de arquivos; Se o post for uma imagem, e o usuário quiser trocar por vídeo, ele pode trocar, fazendo com que a antiga imagem seja deletada do banco de arquivos; Se o post for um vídeo, e o usuário quiser trocar por imagem, ele pode trocar, fazendo com que a antiga video seja deletada do banco de arquivos;
- O usuário deve começar sem a imagem de perfil no momento de cadastro, mas pode adicionar na futura atulização Caso o usuário já tenha uma imagem em seu perfil, ele pode substituilá ou apagá-la, fazendo com que a antiga imagem seja deletada do banco de arquivos.
- Ao adicionar um arquivo no post, o usuário pode escolher abrir a camera e tirar uma foto, ou pode ir na galeria interna do dispositivo e selecionar apenas um video ou uma imagem.
- Cada vídeo ou imagem não podem exceder 20 MBs. Caso o usuário selecione um arquivo de mídia maior, não é adicionado no campo de upload de pré-visialização automaticamente do formulário.
- O frontend mobile deve ser feito em Flutter;
- O backend deve ser feito em Spring Boot;
- O banco de arquivos deve ser o Claudinary;
- O banco de dados deve ser o PostgreSQL.
- O aplicativo deve ser feito para dispositivos android por enquanto e deve respeitar a resposividade;
- O app deverá ter um cacheamento de arquivos para melhora a performance e a experiência de usuário;
- O backend e o banco de dado não deve ser implantado em nuvem por enquanto;
- Deverá respeitar a LGPD;
- Deverá ter uma tela de login, cadastro, home com o feed de posts, profile com dados de usuário e posts privados separados por tipo de posts (TEXT, IMAGE e VIDEO).
``