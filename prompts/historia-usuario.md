# Prompt História de Usuário 

A seguir foi elebarado instruções usadas auxiliar na criação das histórias de usuário de acordo com o PRD da aplicação inserida. Foi utilizado o assistente de IA conversacional Grok como principal ferrameta de geração de texto.

## Instrução no projeto
```text
Com base no PRD fornecido, gere:

- Histórias de Usuário;
- Requisitos Associados;
- Critérios de Aceitação.

Histórias de Usuário

Crie pelo menos uma história de usuário para cada requisito funcional (RF), seguindo o padrão:

- Como [papel],
- Quero [ação],
- Para [finalidade].

Requisitos Associados

Para cada história, associe:

- Requisitos Funcionais (RF)
- Requisitos Não Funcionais (RNF)
- Regras de Negócio (RN)
- Utilizar tabela no formato:

| Requisitos Funcionais | Requisitos Não Funcionais | Regras de Negócio |
|----------------------|--------------------------|------------------|
| [RF001]              | [RNF001], [RNF002]       | [RN001], [RN002] |

Critérios de Aceitação:

Para cada história de usuário, definir critérios de aceitação no formato:

- Dado que [contexto],
- Quando [ação],
- Então [resultado esperado].

Regras Gerais:

- As histórias devem ser pequenas, independentes e entregáveis;
- Evite agrupar múltiplas funcionalidades em uma única história;
- Utilizar markdown;
- Garantir consistência com o PRD;
- Não inventar informações fora do escopo;
- Quero a resposta em formato .md.
```

## PRD Incluso (o que foi mandado no chat)

```text

# Âmago

O Âmago é uma rede social criada para compartilhar memórias de momentos íntimos já vividos, despertando aquele gostinho do passado, profundo e marcante, que merece ser revivido mais uma vez.

O projeto, antes chamado de *Âmago*, foi refatorado para que o aplicativo não seja apenas uma rede social de criação de posts, mas uma plataforma que traga mais significado aos usuários, priorizando práticas de gestão de projeto, qualidade de software, uso de IA e clareza arquitetural.

# RF001

## Caso de Uso: 

Registrar Conta

## Descrição: 

O sistema deve permitir que um novo usuário registre uma nova conta.  

## Atores: 

Usuário Não Autenticado  

## Requisito de Dependência: 

Nenhum

## Dados de Entrada:

| Nome      | Tipo de Dado    | Obrigatório | Propriedade/Regra                          |
|-----------|-----------------|-------------|--------------------------------------------|
| name     | String           | Sim         | Máximo 225 caracteres                         |
| email    | String           | Sim         | Formato de e-mail válido e único no sistema, Máximo 225 caracteres   |
| password | String           | Sim         | Entre 6 e 10 caracteres                       |

## Dados de Saída

- Todos os dados de usuário, com exceção de password;
- Campus que podem vir nulos: bio, image e updated_at.

# RF002

Fazer Login

## Descrição: 

O sistema deve permitir que um usuário já cadastrado faça login.

## Atores: 

Usuário Não Autenticado  

## Requisito de Dependência: 

[RF001](./RF001.md)

## Dados de Entrada:

| Nome      | Tipo de Dado    | Obrigatório | Propriedade/Regra               |
|-----------|-----------------|-------------|---------------------------------|
| email     | String          | Sim        | Formato de e-mail, Máximo 225 caracteres                |
| password  | String          | Sim        | Entre 6 e 10 caracteres          |

## Dados de Saída

- Token de autenticação.

# RF003

Editar Perfil

## Descrição: 

O sistema deve permitir que os usuários já registrados possam editar dados de perfil.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)

## Dados de Entrada:

| Nome      | Tipo de Dado    | Obrigatório | Propriedade/Regra               |
|-----------|-----------------|-------------|---------------------------------|
| name      | String          | Não         | Máximo 225 caracteres           |
| image     | String          | Não         | Formato de e-mail, Máximo 225 caracteres                |
| bio       | String          | Não         | Entre 6 e 10 caracteres          |

## Dados de Saída

- Todos os dados de usuário, com exceção de password;
- Campo updated_at preenchido.

# RF004

Apagar Conta

## Descrição: 

O sistema deve permitir que os usuários já registrados possam apagar sua conta.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)

## Dados de Entrada:

| Nome      | Tipo de Dado    | Obrigatório | Propriedade/Regra               |
|-----------|-----------------|-------------|---------------------------------|
| id        | uuid            | Sim         | único                           |

## Dados de Saída

- Sem dados de saída.

# RF005

Detalhar Perfil

## Descrição: 

O sistema deve permitir que os usuários já registrados possam detalhar perfis de usuário.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)

## Dados de Entrada:

| Nome      | Tipo de Dado    | Obrigatório | Propriedade/Regra               |
|-----------|-----------------|-------------|---------------------------------|
| id        | uuid            | Sim         | único                           |

## Dados de Saída

- Todos os dados de usuário, com exceção de password;

# RF006

Fazer Logout

## Descrição: 

O sistema deve permitir que os usuários já registrados possam fazer logout, ou seja, sair do sistema.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)

## Dados de Entrada:

- Sem dados de entrada

## Dados de Saída

- Todos os dados de usuário, com exceção de password;

# RF007

Cadastrar Post

## Descrição: 

O sistema deve permitir que os usuários já registrados possam cadastrar um novo post.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)

## Dados de Entrada:

| Nome         | Tipo de Dado              | Obrigatório | Propriedade/Regra                          |
|--------------|---------------------------|-------------|--------------------------------------------|
| title       | String                   | Sim        | Máximo 255 caracteres                      |
| description | String (Text)            | Sim        | Texto livre                                |
| post_type   | Enum (TEXT, IMAGE, VIDEO)| Não        | Default: TEXT                              |
| file        | File (Image/Video)       | Não        | Máximo 20 MB, apenas 1 arquivo             |

## Dados de Saída

- Todos os dados do post com o id, name e image de usuário;
- Link de file em String.

# RF008

Editar Post

## Descrição: 

O sistema deve permitir que os usuários já registrados possam editar um post já cadastrado.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)
[RF007](./RF007.md)

## Dados de Entrada:

| Nome         | Tipo de Dado              | Obrigatório | Propriedade/Regra                          |
|--------------|---------------------------|-------------|--------------------------------------------|
| title       | String                   | Não        | Máximo 255 caracteres                      |
| description | String (Text)            | Não        | Texto livre                                |
| post_type   | Enum (TEXT, IMAGE, VIDEO)| Não        |                                            |
| file        | File (Image/Video)       | Não        | Máximo 20 MB, apenas 1 arquivo             |

## Dados de Saída

- Todos os dados do post com o id, name e image de usuário;
- Link de file em String;
- Campo updated_at preenchido.

# RF009

Apagar Post

## Descrição: 

O sistema deve permitir que os usuários já registrados possam apagar um post já cadastrado.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)
[RF005](./RF007.md)

## Dados de Entrada:

| Nome         | Tipo de Dado              | Obrigatório | Propriedade/Regra                          |
|--------------|---------------------------|-------------|--------------------------------------------|
| id        | uuid            | Sim         | único                           |


## Dados de Saída

- Sem dados de saída.

# RF010

Detalhar Post

## Descrição: 

O sistema deve permitir que os usuários já registrados possam detalhar um post já cadastrado.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)
[RF005](./RF007.md)

## Dados de Entrada:

| Nome         | Tipo de Dado              | Obrigatório | Propriedade/Regra                          |
|--------------|---------------------------|-------------|--------------------------------------------|
| id           | uuid            | Sim         | único                           |


## Dados de Saída

- Todos os dados do post com o id, name e image de usuário;

# RF011

Listar Post

## Descrição: 

O sistema deve permitir que os usuários já registrados possam listem todos os posts já cadastrado.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)
[RF007](./RF005.md)

## Dados de Entrada:

- Sem dados de entrada

## Dados de Saída

- Lista de todos os dados do post com o id, name e image de usuário.

# RF012

Filtrar Posts por Tipo de Arquivo

## Descrição: 

O sistema deve permitir que os usuários já registrados possam listar posts por tipo de arquivo.

## Atores: 

Usuário Autenticado  

## Requisito de Dependência: 

[RF002](./RF002.md)
[RF007](./RF005.md)

## Dados de Entrada:

| Nome         | Tipo de Dado              | Obrigatório | Propriedade/Regra                          |
|--------------|---------------------------|-------------|--------------------------------------------|
| id           | uuid            | Sim         | único                           |
| post_type   | Enum (TEXT, IMAGE, VIDEO)| Sim        |                              |


## Dados de Saída

- Lista de post com todos os dados por tipo com o id, name e image de usuário.

# RNF001

O sistema deve respeitar integralmente a LGPD (consentimento, direito ao esquecimento e proteção de dados).

## Categoria

Conformidade

# RNF002

Frontend desenvolvido em Flutter para Android, com layout responsivo.

## Categoria

Usabilidade / Compatibilidade

# RNF003

Backend desenvolvido em Spring Boot com autenticação via JWT.

## Categoria

Segurança / Compatibilidade

# RNF004

Implementar cacheamento de arquivos para melhorar performance e UX.

## Categoria

Desempenho / Usabilidade

# RNF005

Banco de dados PostgreSQL em ambiente local.

## Categoria

Compatibilidade

# RNF006

Armazenamento de arquivos via Cloudinary.

## Categoria

Capacidade


# RNF007 

As senhas dos usuários devem ser armazenadas no banco de dados de forma criptografada (hashing seguro, utilizando algoritmo como BCrypt ou Argon2). Nunca deve ser armazenada a senha em texto plano.

## Categoria

Segurança


# RNF008

O sistema deve utilizar paginação baseada em cursor para carregamento de listas (feed, comentários, seguidores), evitando o uso de paginação por offset.

## Categoria

Desempenho

# RNF009

O sistema deve utilizar mecanismo de cache para armazenar dados frequentemente acessados, como feed de usuários e perfis, utilizando tecnologias como Redis.

## Categoria

Escalabilidade

# RNF010

O sistema deve realizar carregamento progressivo de conteúdo (lazy loading), priorizando a exibição inicial de versões leves de mídia.

## Categoria

Usabilidade

# RNF011

O código do sistema deve ser estruturado de forma modular, facilitando manutenção, testes e evolução.

## Categoria

Manutenibilidade

# RN001

A senha deve ter no mínimo 6 e no máximo 10 caracteres.

# RN002

O e-mail deve ser único no sistema e seguir formato válido.

# RN003

Um usuário pode ter zero ou vários posts. Cada post pertence a exatamente um usuário.

# RN004

Ao atualizar post ou perfil com novo arquivo, o arquivo anterior deve ser removido do Cloudinary.

# RN005

Ao remover post ou conta, todos os arquivos associados devem ser deletados do Cloudinary.

# RN006

O usuário inicia o cadastro sem imagem de perfil.

# RN007

Apenas o dono do post pode editar ou excluir o mesmo.

# RN008

Arquivos de mídia enviados devem ter no máximo 20 MB.

# RN009

Ao atuliazar um post, o usuário pode substituir imagem por vídeo, vídeo por imagem ou remover o arquivo de mídia. Caso seja somente um post de texto, o usuário pode adicionar um arquivo de mídia (imagem ou vídeo).

# RN010

Os post de vídeo devem ser iniciados ao rolar a tela com áudio, caso tenha áudio, e podem ser pausados pelos usuários.

# CT001

[Registrar Conta - RN001](../requisitos/funcionais/RF001.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Cadastro com todos os dados válidos                    | name="Lázaro", email="lazaro@test.com", password="123456"    | Conta criada com sucesso. Retorna todos os dados do usuário (exceto password). bio, image e updated_at podem ser nulos. |
| E-mail já existente no sistema                         | email="lazaro@test.com" (já cadastrado)                      | Erro: "E-mail já existe" (RN002)                            |
| Senha com menos de 6 caracteres                        | password="12345"                                             | Erro: "Senha deve ter entre 6 e 10 caracteres" (RN001)      |
| Senha com mais de 10 caracteres                        | password="12345678901"                                       | Erro: "Senha deve ter entre 6 e 10 caracteres" (RN001)      |
| E-mail em formato inválido                             | email="lazaro@invalid"                                       | Erro: "Formato de e-mail inválido" (RN002)                  |
| Cadastro sem informar o nome                           | name=""                                                      | Erro: "Nome é obrigatório"                                  |
| Cadastro sem informar o e-mail                         | email=""                                                     | Erro: "E-mail é obrigatório"                                |
| Cadastro sem informar a senha                          | password=""                                                  | Erro: "Senha é obrigatória"                                 |

# CT002

[Fazer Login - RN002](../requisitos/funcionais/RF002.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Login com credenciais válidas                          | email="lazaro@test.com", password="123456"                   | Login bem-sucedido. Retorna token de autenticação           |
| Login com senha incorreta                              | password errado                                              | Erro: "E-mail ou senha inválidos"                           |
| Login com e-mail não cadastrado                        | email inexistente                                            | Erro: "E-mail ou senha inválidos"                           |
| Login com e-mail vazio                                 | email=""                                                     | Erro: "E-mail é obrigatório"                                |
| Login com senha vazia                                  | password=""                                                  | Erro: "Senha é obrigatória"                                 |
| Tentativa de login sem estar autenticado (já logado)   | usuário já autenticado tenta login novamente                 | Erro: "Usuário já está autenticado"                         |

# CT003

[Editar Perfil - RN003](../requisitos/funcionais/RF003.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Edição de nome e bio com sucesso                       | name="Novo Nome", bio="Minha bio atualizada"                 | Perfil atualizado com updated_at preenchido                 |
| Atualização de imagem de perfil                        | image=nova_imagem.jpg (15MB)                                 | Imagem atualizada e antiga removida do Cloudinary (RN004)   |
| Remover imagem de perfil existente                     | image=null                                                   | Imagem removida do Cloudinary e campo image fica nulo (RN004)|
| Edição apenas do nome                                  | name="Novo Nome"                                             | Apenas nome atualizado                                      |
| Edição apenas da bio                                   | bio="Nova biografia"                                         | Apenas bio atualizada                                       |
| Edição com imagem maior que 20MB                       | image=arquivo_25MB.jpg                                       | Erro: "Arquivo excede o limite de 20 MB" (RN008)            |
| Tentativa de editar perfil sem autenticação            | sem token                                                    | Erro: "Usuário não autenticado"                             |

# CT004

[Apagar Conta - RN004](../requisitos/funcionais/RF004.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Apagar própria conta com sucesso                       | id=uuid_da_conta_logada                                      | Conta apagada com sucesso. Todos posts e arquivos removidos do Cloudinary (RN005) |
| Apagar conta que possui vários posts e arquivos        | id=uuid_da_conta_com_posts                                   | Conta, todos os posts e arquivos deletados (RN005)          |
| Tentativa de apagar conta sem estar autenticado        | sem token                                                    | Erro: "Usuário não autenticado"                             |
| Apagar conta com id inválido ou inexistente            | id=uuid_inexistente                                          | Erro: "Conta não encontrada"                                |

# CT005

[Detalhar Perfil - RN005](../requisitos/funcionais/RF005.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Detalhar o próprio perfil                              | id=uuid_do_usuario_logado                                    | Retorna todos os dados do usuário (exceto password)         |
| Detalhar perfil de outro usuário                       | id=uuid_de_outro_usuario                                     | Retorna dados públicos do outro usuário                     |
| Detalhar perfil inexistente                            | id=uuid_inexistente                                          | Erro: "Usuário não encontrado"                              |
| Detalhar perfil sem estar autenticado                  | sem token

# CT006

[Fazer Logout - RN006](../requisitos/funcionais/RF006.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Realizar logout com sucesso                            | usuário autenticado                                          | Logout realizado com sucesso. Token invalidado              |
| Tentativa de logout sem estar autenticado              | sem token                                                    | Erro: "Usuário não autenticado"                             |

# CT007

[Cadastrar Post - RN007](../requisitos/funcionais/RF007.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Cadastrar post somente com texto                       | title="Minha memória", description="Texto aqui", post_type="TEXT" | Post criado com sucesso                                     |
| Cadastrar post com imagem válida                       | title, description, file=imagem.jpg (15MB)                   | Post criado com link do arquivo no Cloudinary               |
| Cadastrar post com vídeo válido                        | title, description, file=video.mp4 (18MB)                    | Post criado com link do vídeo no Cloudinary                 |
| Cadastrar post com arquivo maior que 20MB              | file=video_25MB.mp4                                          | Erro: "Arquivo excede o limite de 20 MB" (RN008)            |
| Cadastrar post sem título                              | title=""                                                     | Erro: "Título é obrigatório"                                |
| Cadastrar post sem descrição                           | description=""                                               | Erro: "Descrição é obrigatória"                             |
| Cadastrar post sem estar autenticado                   | sem token                                                    | Erro: "Usuário não autenticado"                             |

# CT008

[Editar Post - RN008](../requisitos/funcionais/RF008.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Editar título e descrição com sucesso                  | title="Novo título", description="Texto atualizado"          | Post atualizado com updated_at preenchido                   |
| Trocar arquivo de texto para imagem                    | novo file=imagem.jpg                                         | Post atualizado e arquivo antigo removido (RN004, RN009)    |
| Trocar arquivo de imagem para vídeo                    | novo file=video.mp4                                          | Post atualizado e arquivo anterior removido (RN004, RN009)  |
| Remover arquivo de mídia do post (deixar só texto)     | file=null                                                    | Post atualizado sem arquivo (RN009)                         |
| Editar post que não pertence ao usuário logado         | post de outro usuário                                        | Erro: "Apenas o dono pode editar o post" (RN007)            |
| Editar post sem estar autenticado                      | sem token                                                    | Erro: "Usuário não autenticado"                             |
| Editar post inexistente                                | id=uuid_inexistente                                          | Erro: "Post não encontrado"                                 |

# CT009

[Apagar Post - RN009](../requisitos/funcionais/RF009.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Apagar próprio post com sucesso                        | id=post_do_usuario_logado                                    | Post apagado e arquivo removido do Cloudinary (RN005)       |
| Apagar post que possui arquivo de mídia                | id=post_com_arquivo                                          | Post e arquivo deletados do Cloudinary (RN005)              |
| Apagar post de outro usuário                           | id=post_de_outro_usuario                                     | Erro: "Apenas o dono pode apagar o post" (RN007)            |
| Apagar post inexistente                                | id=uuid_inexistente                                          | Erro: "Post não encontrado"                                 |
| Apagar post sem estar autenticado                      | sem token                                                    | Erro: "Usuário não autenticado"                             |

# CT010

[Detalhar Post - RN010](../requisitos/funcionais/RF010.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Detalhar próprio post                                  | id=post_do_usuario_logado                                    | Retorna todos os dados completos do post + dados do usuário |
| Detalhar post de outro usuário                         | id=post_de_outro_usuario                                     | Retorna dados do post (visualização permitida)              |
| Detalhar post inexistente                              | id=uuid_inexistente                                          | Erro: "Post não encontrado"                                 |
| Detalhar post sem estar autenticado                    | sem token                                                    | Erro: "Usuário não autenticado"                             |

# CT011

[Listar Post - RN011](../requisitos/funcionais/RF011.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Listar todos os posts do usuário logado (com posts)    | usuário com vários posts                                     | Retorna lista completa de todos os posts do usuário         |
| Listar posts de usuário que não possui nenhum post     | usuário novo sem posts                                       | Retorna lista vazia                                         |
| Listar posts sem estar autenticado                     | sem token                                                    | Erro: "Usuário não autenticado"                             |

# CT012

[Filtrar Posts por Tipo de Arquivo - RN012](../requisitos/funcionais/RF012.md) 

| Descrição                                              | Entrada                                                      | Resultado Esperado                                           |
|--------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| Filtrar posts do tipo IMAGE                            | post_type="IMAGE"                                            | Retorna apenas posts do tipo IMAGE                          |
| Filtrar posts do tipo VIDEO                            | post_type="VIDEO"                                            | Retorna apenas posts do tipo VIDEO                          |
| Filtrar posts do tipo TEXT                             | post_type="TEXT"                                             | Retorna apenas posts do tipo TEXT                           |
| Filtrar com tipo de post inválido                      | post_type="INVALID"                                          | Erro: "Tipo de post inválido"                               |
| Filtrar sem informar o tipo (campo vazio)              | post_type=""                                                 | Erro: "Tipo de post é obrigatório"                          |
| Filtrar posts de usuário sem posts daquele tipo        | post_type="VIDEO" (usuário sem vídeos)                       | Retorna lista vazia                                         |
```


