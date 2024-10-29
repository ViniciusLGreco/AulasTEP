# AulasTEP
Repositório com todas as aulas de Tópicos Especiais em Programação.

# Aula 1 - dia 08/08/2024
Não teve aula

# Aula 2
Dia 15/08/2024

Criar conta no GPT
Passo a passo:

Acesse o site da OpenAI: Vá até a página principal da OpenAI: https://platform.openai.com/
Clique em "Sign Up" (Inscreva-se): Geralmente, este botão se encontra no canto superior direito da página.
Preencha as informações solicitadas:
E-mail: Insira um endereço de e-mail válido.
Senha: Crie uma senha forte e segura.
Outras informações: Podem ser solicitados outros dados, como nome completo e organização (se aplicável).
Verifique seu e-mail: A OpenAI enviará um e-mail de verificação para confirmar sua identidade. Clique no link de verificação dentro do e-mail.
Complete o perfil (opcional): Após a verificação, você pode personalizar seu perfil adicionando informações adicionais, como sua área de interesse e como planeja usar as ferramentas da OpenAI.
Comece a usar: Com a conta criada, você terá acesso aos diferentes produtos e serviços oferecidos pela OpenAI, como o ChatGPT, API da OpenAI e outros.
Criar conta no Groq
https://groq.com/

Trabalhando com ambientes Virtuais no Python
Ambientes virtuais são como "ilhas" isoladas dentro do seu sistema, onde você pode instalar e gerenciar pacotes Python de forma independente para cada projeto. Isso significa que cada projeto terá sua própria versão do Python e suas próprias bibliotecas, evitando conflitos entre diferentes versões e dependências.

Por que usar ambientes virtuais?

Isolamento de projetos: Cada projeto terá seu próprio conjunto de pacotes, evitando conflitos de versão.
Gerenciamento de dependências: Facilita o controle das versões exatas de cada pacote utilizado em um projeto.
Reprodutibilidade: Permite que outros desenvolvedores reproduzam o ambiente do seu projeto com facilidade.
Organização: Mantém seu ambiente Python organizado e livre de confusões.
a) Criando um ambiente virtual local com Python no terminal

python -m venv meu_ambiente # Ativar ambiente - Linux;WSL source meu_ambiente/bin/activate # Ativar ambiente - windows meu_ambiente\Scripts\activate # Instalando pacotes pip install <module name> # Dica. Nomear ambiente como .venv
b) Criando um ambiente virtual local com Python no VSCODE

Testes práticos:
Search Tools GPTs

.Chat com GPT
.Imagem com DALLE-3
.Texto para audio Groq
.Audio para texto
.Chat com Groq

PDF de LLMs(https://github.com/ViniciusLGreco/AulasTEP/blob/main/LLMs.pdf)

# Aula 3
 Modelos LLM, Hugging Face e Ollama

Finalizar Exemplo Docker
Baixar Ferramentas

- Baixar LLM Studio
- Baixar Anything LLM
- Baixar Ollama

Baixar Modelos e salvar na pasta

```d
C:\Users\<SEU_USUARIO>\.cache\lm-studio\models
```

Conhecer os detalhes dos modelos.

# Aula 4


**O que é Engenharia de Prompt**

A Engenharia de Prompts é uma disciplina emergente que se dedica a criar e otimizar instruções textuais, ou "prompts", que direcionam o comportamento dos LLMs para produzir respostas precisas e úteis. Este campo é essencial para maximizar a eficiência e a precisão dos modelos de linguagem, pois determina como esses modelos interpretam e respondem às solicitações dos usuários.
---

- Formulação de entradas que orientam o comportamento dos modelos de linguagem.

- A criação de prompts eficazes é um processo interativo que inclui planejamento, testes e refinamentos contínuos.

- A EP deve prezar pela clareza, neutralidade e imparcialidade.
  
  - Escolha cuidadosa das palavras para evitar interpretações tendenciosas

- EP inclui a criação e reestruturação de prompts existentes

- Personalização de prompts para diferentes públicos e aplicações

Técnicas Básicas de Engenharia de Prompt

---

Configurações da LLM

- Temperatura - quanto menor a `temperatura`, mais determinísticos são os resultados
- Tokens - cerca de 4 caracteres (english)
- TopP - Se você está procurando respostas exatas e factuais, mantenha isso baixo

---

Prompts Básicos

```d
O céu é
```

Melhorando o contexto:

```d
Complete a sentença:
O céu é
```

---

Isto é melhor? Bem, dissemos ao modelo para completar a frase para que o resultado fique muito melhor, pois segue exatamente o que dissemos para fazer ("complete a frase"). Essa abordagem de projetar prompts ideais para instruir o modelo a executar uma tarefa é chamada de **engenharia de prompt**.

O Exemplo de prompt acima corresponde apenas a uma pergunta direta, em que você está solicitando diretamente ao modelo uma resposta sem nenhum exemplo ou demonstração sobre a tarefa que deseja realizar. Este modelo é conhecido como **Zero-shot Prompting**.
---

Outra técnica popular é a *Few-shot Prompting* onde fornecemos exemplos (ou seja, demonstrações). Os prompts de poucos tiros podem ser formatados da seguinte maneira:

```d
<Pergunta>?
<Resposta>
<Pergunta>?
<Resposta>
<Pergunta>?
<Resposta>
<Pergunta>?
```

---

Lembre-se de que não é necessário usar o formato QA. O formato do prompt depende da tarefa em mãos. 

Exemplo:

- Você pode executar uma tarefa de classificação simples e fornecer exemplares que demonstrem a tarefa da seguinte forma:

Prompt:

```d
Isso é incrível! // Positivo
Isto é mau! // Negativo
Uau, esse filme foi radical! // Positivo
Que espetáculo horrível! //
```

---

 Elementos de um prompt

Um prompt pode conter qualquer um dos seguintes componentes:

- Instrução - o que você deseja que o modelo execute
- Contexto - informações externas ou contexto adicional 
- Dados de entrada - é a entrada ou pergunta para a qual queremos uma resposta
- Indicador de saída - indica o tipo ou formato da saída.

Nem todos os componentes são necessários para um prompt e o formato depende da tarefa em questão. 

---

 Dicas gerais para projetar prompts

Comece Simples

> A especificidade, a simplicidade e a concisão geralmente lhe darão melhores resultados
> Forneça uma instrução
> Experimente instruções diferentes com palavras-chave, contextos e dados diferentes e veja o que funciona melhor para seu caso

Recomendam que as instruções sejam colocadas no início do prompt.

Prompt:

```d
# Instrução #
Traduza o texto abaixo para o espanhol:
Texto: "olá!"
```

---

Especificidade

> Seja muito específico sobre a instrução e a tarefa que deseja que o modelo execute. Quanto mais descritivo e detalhado for o prompt, melhores serão os resultados.

Prompt:

```d
Extraia o nome dos lugares no texto a seguir.
Formato desejado:
Local: <lista_de_nomes_de_empresa_separados_por_vírgula>
Input: "Embora estes desenvolvimentos sejam encorajadores para os investigadores, muito ainda é um mistério. “Muitas vezes temos uma caixa preta entre o cérebro e o efeito que vemos na periferia”, diz Henrique Veiga-Fernandes, neuroimunologista do Centro Champalimaud para o Desconhecido em Lisboa. “Se queremos utilizá-lo no contexto terapêutico, precisamos de facto de perceber o mecanismo."
```

---

Agora utilizando outro formato de saída (JSON).

Prompt:

```d
Extraia o nome dos lugares no texto a seguir.
Formato desejado:
Local: {"local": "{{nome_do_local}}"}
Input: "Embora estes desenvolvimentos sejam encorajadores para os investigadores, muito ainda é um mistério. “Muitas vezes temos uma caixa preta entre o cérebro e o efeito que vemos na periferia”, diz Henrique Veiga-Fernandes, neuroimunologista do Centro Champalimaud para o Desconhecido em Lisboa. “Se queremos utilizá-lo no contexto terapêutico, precisamos de facto de perceber o mecanismo."
```

---

Evite Imprecisões

> Dadas as dicas acima sobre como ser detalhado e melhorar o formato, é fácil cair na armadilha de querer ser muito inteligente sobre os prompts e potencialmente criar descrições imprecisas.

Por exemplo, você pode estar interessado em aprender o conceito de engenharia de prompt. Você pode tentar algo como:

Prompt:

```d
Explique o conceito de engenharia de prompt. Mantenha a explicação curta, apenas algumas frases, e não seja muito descritivo.
```

---

Não está claro no prompt acima quantas frases usar e qual estilo. Você ainda pode obter uma boa resposta com o prompt acima, mas o melhor prompt seria aquele que é muito específico, conciso e direto ao ponto. Algo como:

Prompt:

```d
Use 2 a 3 frases para explicar o conceito de engenharia de prompt a um aluno do ensino médio.
```

---

Fazer ou não fazer?

> Outra dica comum ao criar prompts é evitar dizer o que não fazer, mas dizer o que fazer. Isso incentiva mais especificidade e concentra-se nos detalhes que levam a boas respostas do modelo.
> Aqui está um exemplo de um chatbot de recomendação de filme falhando exatamente no que eu não quero que ele faça por causa de como escrevi a instrução -- focando no que não fazer.

Prompt:

```d
O agente a seguir recomenda filmes para um cliente. NÃO PEÇA INTERESSES. NÃO PEÇA INFORMAÇÕES PESSOAIS.
Cliente: Por favor, recomende um filme baseado nos meus interesses.
Agente:
```

---

Aqui está um prompt melhor:

Prompt:

```d
O agente a seguir recomenda filmes para um cliente. O agente é responsável por recomendar um filme dos principais filmes de tendências globais. Deve abster-se de perguntar aos usuários sobre suas preferências e evitar pedir informações pessoais. Se o agente não tiver um filme para recomendar, ele deve responder "Desculpe, não foi possível encontrar um filme para recomendar hoje.".
Cliente: Por favor, recomende um filme baseado nos meus interesses.
Agente:
```

---

 Exemplos de Prompts

 Resumo de texto

Uma das tarefas padrão na geração de linguagem natural é o resumo de texto.

Digamos que estou interessado em aprender sobre antibióticos, poderia tentar um prompt como este:

---

Prompt:

```d
Explique os antibióticos
A:
```

O "A:" é um formato de prompt explícito usado para responder perguntas. Neste exemplo, não está claro como isso é útil ou não, mas deixaremos isso para exemplos posteriores.

---

Vamos apenas supor que a resposta obtida ainda é muita informação e queremos resumi-la ainda mais. Na verdade, podemos instruir o modelo a resumir em uma frase da seguinte forma:

Prompt

```d
A: <resposta anterior>
Q: **Explique em uma frase.**
A:
```

---

 Extração de Informações

Embora os modelos de linguagem sejam treinados para executar a geração de linguagem natural e tarefas relacionadas, eles também são muito capazes de realizar classificação e uma série de outras tarefas de processamento de linguagem natural (NLP).

> Veja o exemplo feito anteriormente.

Esse é um recurso poderoso que os desenvolvedores de produtos de IA já estão usando para criar produtos e experiências poderosos.

---

 Resposta a perguntas

Uma das melhores maneiras de fazer com que o modelo responda de forma específicas é melhorar o formato do prompt. Conforme abordado anteriormente, um prompt pode combinar instruções, contexto, entrada e indicadores de saída para obter melhores resultados.

---

Prompt:

```
Responda a pergunta com base no contexto abaixo. Mantenha a resposta curta e concisa. Responda "Não tenho certeza sobre a resposta" se não tiver certeza da resposta.
Contexto: Teplizumab tem suas raízes em uma empresa farmacêutica de Nova Jersey chamada Ortho Pharmaceutical. Lá, os cientistas geraram uma versão inicial do anticorpo, apelidada de OKT3. Originalmente proveniente de camundongos, a molécula foi capaz de se ligar à superfície das células T e limitar seu potencial de morte celular. Em 1986, foi aprovado para ajudar a prevenir a rejeição de órgãos após transplantes renais, tornando-se o primeiro anticorpo terapêutico permitido para uso humano.
Pergunta: De onde veio originalmente o OKT3?
Responder:
```

---

 Classificação de texto

Até agora, usamos instruções simples para executar uma tarefa. Como um engenheiro de prompt, você precisará melhorar o fornecimento de melhores instruções. 

---

Vamos tentar demonstrar isso fornecendo um exemplo de classificação de texto.

Prompt:

```json
Classifique o texto em neutro, negativo ou positivo.
Texto: Acho que a comida estava mais ou menos.
Sentimento:
```

---

Independente da resposta, digamos que o que realmente precisamos é que o modelo dê o rótulo no formato exato que queremos. Como alcançamos isso? 

> Existem diferentes maneiras de fazer isso. Nós nos preocupamos com a especificidade aqui, portanto, quanto mais informações pudermos fornecer, melhores serão os resultados. Podemos tentar fornecer exemplos para especificar o comportamento correto. 

Vamos tentar de novo:

---

Prompt:

```json
Classifique o texto em neutro, negativo ou positivo.
Texto: Acho que as férias estão mais ou menos.
Sentimento: positivo
Texto: Acho que a comida estava mais ou menos.
Sentimento:
```

O modelo utilizado correspondeu com suas expectativas? Qual é o problema aqui? Procure utilizar mais exemplos. Faça um refinamento.

---

 Conversação (Chat)

Talvez uma das coisas mais interessantes que você pode conseguir com a engenharia imediata seja instruir o sistema LLM sobre como se comportar, sua intenção e sua identidade. 

---

Exemplo: vamos criar um sistema de conversação capaz de gerar respostas mais técnicas e científicas às perguntas. 

Prompt:

```json
A seguir, uma conversa com um assistente de pesquisa de IA. O tom assistente é técnico e científico.
Humano: Olá, quem é você?
AI: Saudações! Eu sou um assistente de pesquisa de IA. Como posso te ajudar hoje?
Humano: Você pode me falar sobre a criação de buracos negros?
AI:
```

---

Nosso assistente de pesquisa de IA parece um pouco técnico demais, certo? Ok, vamos mudar esse comportamento e instruir o sistema a dar respostas mais acessíveis.

Prompt:

```json
A seguir, uma conversa com um assistente de pesquisa de IA. As respostas do assistente devem ser fáceis de entender, utilizando um vocabulário acessível por alunos do ensino fundamental.
Humano: Olá, quem é você?
AI: Saudações! Eu sou um assistente de pesquisa de IA. Como posso te ajudar hoje?
Humano: Você pode me falar sobre a criação de buracos negros?
AI:
```

---

Você pode continuar melhorando. Tenho certeza que se você adicionar mais exemplos você pode obter resultados ainda melhores.

---

 Geração de Código

Uma aplicação em que os LLMs são bastante eficazes é a geração de código. O Copilot é um ótimo exemplo disso.

Em alguns modelos nem é preciso descrever como a IA deve se comportar. Apenas insira o prompt e ele lhe retornará com uma resposta em uma determinada linguagem de programação.

---

Contudo, aqui vamos fornecer um prompt para o sistema:
System:

```json
Você é um programador experiente. Ajude os usuários a criarem código que sejam simples e eficientes. Se o usuário não especificar a linguagem de programação, sempre utilize javascript como base.
```

Prompt:

```json
/*
Pergunte ao usuário o nome dele e diga "Olá"
*/
```

Você pode ver que nem precisamos especificar a linguagem a ser usada.

---

Aprimorando o prompt conseguimos resultados muito poderosos.

```json
Tabela departamentos, colunas = [DepartmentId, DepartmentName]
Alunos da tabela, colunas = [DepartmentId, StudentId, StudentName]
Crie uma consulta MySQL para todos os alunos do Departamento de Ciência da Computação
```

---

 Raciocínio

os LLMs atuais lutam para executar tarefas de raciocínio, portanto, isso requer técnicas de engenharia de prompt ainda mais avançadas.

Prompt:

```json
Os números ímpares neste grupo somam um número par: 15, 32, 5, 13, 82, 7, 1.
A:
```

Isso é incorreto! Vamos tentar melhorar isso melhorando o prompt.

---

Prompt:

```json
Os números ímpares neste grupo somam um número par: 15, 32, 5, 13, 82, 7, 1.
Resolva dividindo o problema em etapas. Primeiro, identifique os números ímpares, some-os e indique se o resultado é par ou ímpar.
```

---

 Principais Técnicas

# Zero-shot & Few-shot Prompting

O conceito de zero-shot prompting refere-se à capacidade de um modelo de linguagem de entender e executar uma tarefa sem ter recebido exemplos específicos dessa tarefa anteriormente.

> A palavra "shot" nesse contexto se refere a "exemplo", e "prompting" seria a "criação de prompts".

---

# Chain-of-Thought Prompting

O conceito de Chain-of-Thought Prompting pode ser traduzido como "Criação de prompts com Cadeia de Pensamento".

---

Prompt

```json
P: Um paciente chega ao hospital com sintomas de febre, tosse e dificuldade para respirar. Primeiro, o médico realiza um exame físico. Em seguida, solicita exames de sangue e uma radiografia do tórax. Após analisar os resultados, o médico diagnostica pneumonia. Explique a sequência de passos que o médico seguiu para diagnosticar a pneumonia.

R: O médico realizou um exame físico para avaliar os sintomas. Depois, solicitou exames de sangue e uma radiografia do tórax para obter mais informações. Com os resultados, diagnosticou pneumonia. A sequência de passos é: exame físico, exames de sangue, radiografia do tórax, diagnóstico de pneumonia. (CoT aplicado)

P: Um paciente chega com dor abdominal aguda. O médico primeiro faz um exame físico. Depois, pede exames de sangue e uma tomografia computadorizada. Com os resultados, identifica uma apendicite. Quais passos o médico seguiu para diagnosticar a apendicite?
```

---

> Ele propõe que podemos obter respostas muito mais precisas quando demonstramos aos modelos, no próprio prompt, a forma exata de raciocinar, dando uma resposta completa como exemplo, incluindo o passo a passo para chegar a ela.

Obs. Essa técnica também é chamada de Few-shot Chain-of-Thought Prompting (traduzindo, "Criação de prompts com Cadeia de Pensamento com alguns exemplos")

---

# Zero-shot Chain-of-Thought

Poucos meses depois do artigo sobre Few-shot Chain-of-Thought, uma equipe composta de cientistas da Universidade de Tóquio, no Japão, e do Google publicou outro artigo propondo que modelos de linguagem não precisariam necessariamente de toda essa explicação e exemplos (few-shot) para darem uma resposta correta.

> E que, para fazer o modelo se comportar com uma cadeia de pensamento (Chain-of-Thought), bastaria utilizar a frase "Let's think step by step" (em português, "Vamos pensar passo a passo") no final do prompt.

---

# Self-consistency (Autoconsistência)

Essa estratégia simples também proposta pela equipe do Google consiste em usar a técnica de Few-shot Chain-of-Thought para obter um conjunto de diversas respostas para um mesmo prompt e, então, escolher a resposta que apareceu o maior número de vezes.

> Um prompt é passado várias vezes ao modelo (em janelas diferentes de chat ou em diferentes chamadas à API, por exemplo), e diversas respostas diferentes são geradas, contudo,  seleciona apenas aquela mais recorrente.

---

# Chain-of-Verification

Na Chain-of-Verification, após o modelo gerar uma resposta inicial a um prompt, são formuladas perguntas de seguimento para ajudar a verificar a veracidade e a precisão da resposta inicial.
Prompt

```json
Por favor, responda inicialmente de forma concisa à minha pergunta. Em seguida, faça perguntas sobre a resposta inicial e verifique os fatos apresentados nessas respostas. Exponha as perguntas e respostas do processo de verificação detalhadamente e, com base nessa análise, reformule uma resposta final mais precisa e fundamentada para a minha <pergunta> (CoVE aplicado)

<pergunta> Quando o Ayrton Senna morreu? <pergunta>
```

---

# Geração com Recuperação Aprimorada (RAG)

Pesquisadores de Meta IA introduziram um método chamado Geração com Recuperação Aprimorada (RAG) para lidar com tarefas intensivas em conhecimento. O RAG combina um componente de recuperação de informações com um modelo gerador de texto.

---

# React - Razão e Ação

Yao et al., 2022 introduziu uma estrutura em que LLMs são usados para gerar rastros de raciocínio e ações específicas de tarefas de maneira intercalada. A geração de rastros de raciocínio permite que o modelo induza, rastreie e atualize planos de ação e até mesmo trate de exceções. 

> A etapa de ação permite interagir e coletar informações de fontes externas, como bases de conhecimento ou ambientes

---

 Engenharia de Prompt

Bruno Picinini e Sandeco

# Técnicas a serem aplicadas

---

> Definir uma Persona - identidade

```json
PROMPT: Você agora é um profissional da educação na área da computação para crianças e adolescentes, tem a missão de ensinar conceitos de ciência da computação e habilidades de programação de maneira acessível e envolvente. Sua habilidade em transformar tópicos complexos em conteúdos lúdicos e práticos incentiva a criatividade e a resolução de problemas nos jovens. Com seu conhecimento técnico em linguagens de programação e tecnologias emergentes, você está sempre atento às necessidades e interesses dos alunos, criando um ambiente inclusivo e motivador que promove o pensamento crítico e a inovação. Sua capacidade de adaptar o conteúdo para diferentes faixas etárias e níveis de habilidade garante que todos os estudantes possam avançar de forma significativa e divertida no mundo digital.
```

---

> Uso de delimitadores

```xml
PROMPT: Leia os textos delimitados por <texto1> e <texto2> e escreva um novo texto relacionando-os.

<texto1>  
Os aviões são máquinas complexas e maravilhosas que revolucionaram o transporte e a comu- nicação global. Capazes de percorrer grandes distâncias em curtos períodos, eles conectam pessoas, culturas e economias de maneira inédita. Utilizando princípios da aerodinâmica, os aviões se sustentam no ar graças à forma de suas asas, que criam uma diferença de pressão que permite o voo.

</texto1>  
<texto2>  
A viagem ao espaço representa um dos maiores avanços da humanidade, permitindo a explo-

ração de fronteiras além da Terra. </texto2>
```

---

> Forneça Exemplos

```json
PROMPT:

Escreva um e-mail formal para um cliente sobre o atraso distribuição de insumos. Utilize o e-mail delimitado em <exemplo> como referência para o tom e a estrutura.

<exemplo>  
Prezado Sr. Silva,  
Gostaríamos de informá-lo sobre um atraso inesperado na entrega do seu projeto. Devido a imprevistos técnicos, não conseguiremos concluir o trabalho dentro do prazo inicialmente estipulado. Estamos trabalhando arduamente para resolver estas questões e estimamos que a entrega será feita até o final da próxima semana. Pedimos desculpas pelo inconveniente e agradecemos a sua compreensão.  
Atenciosamente,  
João Pereira  
Gerente de Projetos

</exemplo>  
Agora, escreva o e-mail
```

---

Considerar os seguintes pontos em prompts mais complexos:

> Objetivo - o que espera alcançar

> Modelo - formato do resultado

> Contexto - descrever o estado atual (problema)

> Refinamentos

---

> Além de incluir, quando couber, controle de:

- Nível de complexidade do texto: Definir escala 
- Entonação  - definir níveis
- Controle de sentimento - definir escalas
- Perpectiva - 1, 2 ou terceira pessoa.
- Controle de foco no assunto. Definir escala. Ex. Escala de Foco: 1 o foco é amplo e 10 o foco é muito restrito
- Nível de detalhe - criar escala
- etc

---

# Processo para desenvolver PROMPTs mais completos

- Definir critérios e tarefas de sucesso
  - Desempenho e precisão: Quão bem o modelo executa o processo  
  - Latência: tempo de resposta do modelo  
  - Preço: qual seu orçamento
- Desenvolver casos de teste
- Escrever o prompt ininical  
  - Processo constante de refinamento
- Teste-o contra exemplos
- Refine o prompt
- Ponha-o em produção

Veja o arquivo: obsidian://open?vault=TEP&file=Modelo%20de%20Agente%20com%20XML.pdf

---

 Dicas

Verificar o tamanho máximo do prompt. 

> Tamanho do Prompt: 18k Caracteres (GPT)

Transformar a base de conhecimento em arquivos .json
Utilizar Recompensas e Punições
Estruturação de documentos longos. 

- Posicione antes das instruções.

---

# Aprenda ou Revise:

- Markdown {{PDF}}
- JSON - https://quickref.me/json.html

---

 Exercícios

Para consolidar os conceitos apresentados, aqui estão alguns exercícios práticos para você aplicar as técnicas básicas da engenharia de prompts. 

Para cada exercício anote o prompt inicial e a resposta obtida, o prompt final (que lhe agradou) e a resposta obtida. Segue modelo

Prompt:

```d
O Céu é
```

Saída:

```d
Azul
```

---

1. Crie um prompt simples pedindo ao modelo para escrever uma carta de recomendação sem fornecer nenhum contexto adicional. Depois, revise o prompt adicionando detalhes sobre o destinatário e o propósito da carta. Como o contexto influenciou a qualidade da resposta?
2. Defina uma persona para um assistente virtual que auxilia clientes de uma livraria. Crie um prompt que utilize essa persona para responder clientes e indicar livros. Avalie como a definição de persona impacta a resposta do modelo.
3. Escreva um prompt vago pedindo ao modelo para descrever um cenário futurista, sem dar detalhes. Depois, reescreva o prompt com instruções claras e específicas sobre o tipo de cenário e detalhes a serem incluídos. Avalie a importância da clareza nas instruções.
4. Desenvolva um prompt inicial para gerar uma breve biografia de uma figura histórica a ser definida por você. Analise a resposta e refine o prompt adicionando detalhes, informações adicionais e ajustando as instruções. Realize várias iterações e observe como cada refinamento melhora a precisão da resposta.
5. Desenvolva um prompt personalizado para um posto de gasolina. Use todas as técnicas discutidas neste capítulo para otimizar o prompt. Avalie a eficácia do prompt baseado na resposta do modelo e faça os ajustes necessários. Utilize o ChatGPT ou outro serviço à sua escolha para auxiliar na geração de um prompt interativo.
6. Escreva dois prompts sobre o mesmo tema, mas com diferentes entonações: um formal e outro casual. Utilize a escala de entonação de 1 a 10.
7. Crie dois prompts para gerar textos com diferentes sentimentos sobre o mesmo assunto. Utilize a escala de sentimento de 1 a 10.
8. Crie três prompts sobre o mesmo tema, cada um utilizando uma perspectiva diferente: primeira, segunda e terceira pessoa. Utilize a escala de perspectiva de 1 a 3.
9. Escreva dois prompts que descrevam a mesma cena, mas com diferentes níveis de detalhe. Utilize a escala de nível de detalhe de 1 a 10.

---

 Estude as Referências

- https://www.promptingguide.ai/

- https://learn.microsoft.com/pt-br/azure/ai-services/openai/concepts/prompt-engineering

- https://www.alura.com.br/artigos/engenharia-prompt?srsltid=AfmBOop4oY145iWN7Mu-BxxPihU-kpTdCqJmhkx7qBRk0jFt-gt0j-JP

- Crédito de 200 Dolares - DigitalOcean - [DigitalOcean | Cloud Infrastructure for Developers](https://www.digitalocean.com/?refcode=fd053d06228b&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=CopyPaste)

**Ollama Course**

- https://www.youtube.com/watch?v=9KEUFe4KQAI&list=PLvsHpqLkpw0fIT-WbjY-xBRxTftjwiTLB

- **Livro do Sandeco**
- 
# Aula 5

Aula 5 -Conceitos de RAG com Langchain e Langflow
Atividades com Agentes CREW AI

Agentes de IA com CrewAI e Llama3 usando a API Groq

Este exemplo demonstra como criar agentes de IA usando a biblioteca CrewAI, o modelo Llama3 e a API Groq em Python. O objetivo é fornecer uma estrutura básica para configurar e executar agentes de IA.

Requisitos
Antes de começar, certifique-se de ter os seguintes requisitos instalados:

Python 3.8 ou superior
Biblioteca CrewAI
Acesso à API Groq para o modelo Llama3
pip para gerenciar pacotes Python
Instalação
Clone o repositório:

git clone https://github.com/viniciusds2020/ai_crewai_starter_template.git
cd ai_crewai_starter_template
Crie um ambiente virtual (opcional, mas recomendado):

python -m venv venv
source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
Instale as dependências:

pip install -r requirements.txt
Configuração
Obtenha uma chave de API da Groq para acessar o modelo Llama3. Registre-se no site da Groq e siga as instruções para gerar a chave de API.

Crie um arquivo .env na raiz do projeto e adicione sua chave de API:

GROQ_API_KEY=your_api_key_here
Teste sua configuração para verificar se está carregando corretamente o arquivo .env

import os
from dotenv import load_dotenv

# Carrega as variáveis de ambiente do arquivo .env
load_dotenv()

# Verifica se a chave foi carregada corretamente
groq_api_key = os.getenv('GROQ_API_KEY')
if groq_api_key is None:
    print("A chave da API não foi carregada corretamente.")
else:
    print("Chave da API carregada:", groq_api_key)
Uso
O arquivo principal main.py contém a lógica para inicializar e executar o agente de IA. Para iniciar o agente, execute:

python main.py
Estrutura do Projeto
.
├── README.md
├── requirements.txt
├── main.py
└── .env
README.md: Este arquivo de documentação.
requirements.txt: Arquivo de dependências do Python.
main.py: Script principal que inicializa e executa o agente de IA.
.env: Arquivo contendo a chave de API da Groq.
Fiz alguns pequenos ajustes abaixo para facilar o uso. Revise seu arquivo.

Arquivo agents.py

### Sistemas de multi-agentes de inteligencias artificiais

# Biblioteca
from crewai_tools import tool
from crewai import Agent, Task, Crew
from langchain_groq import ChatGroq
from langchain_community.tools import DuckDuckGoSearchRun

# Modelo LLM - Llama3 
llm = ChatGroq(temperature=0.7,
               groq_api_key='sua-chave-api-groq',
               model_name='llama-3.1-8b-instant') #novo modelo

#se for usar o GPT
#llm = ChatOpenAI(model_name="gpt-4o-mini", temperature=0.3)

# Ferramentas - Busca na internet com DuckDuckGo
@tool('DuckDuckGoSearchRun')
def search_tool(search_query: str):
  ''' Search the web for infotmation on a given topic'''
  return DuckDuckGoSearchRun().run(search_query)

# Topico do blog
topic = "Apple and AI in finance"

# Agentes
researcher = Agent(
    role = "Senior Researcher",
    goal = f"Explore trending technologies in {topic}.",
    backstory = "You are an innovative researher who follows the latest technology",
    verbose = True,
    tools = [search_tool],
    llm = llm,
)

writer = Agent(
    role = "Top Writer",
    goal = f"Create engaging content about {topic}. ",
    backstory = "You are an expert blogger who writes interesting articles.",
    verbose = True,
    tools = [search_tool],
    llm = llm,
)

# Tarefas
research_task = Task(
    description = f"Investigate the latest AI trends in {topic}.",
    expected_output = "A comprehensive 4 paragraphs long report on the latest AI trends.",
    tools = [search_tool],
    agent = researcher,
)

write_task = Task(
    description = f"Write an engaging article on {topic} that focuses on the latest trends.",
    expected_output = f"A comprehensive 4 paragraphs blog on {topic} in markdown format.",
    tools = [search_tool],
    agent = researcher,
    output_file = "my-blog.md"
)

# Orquestrador
crew = Crew(
    agents=[researcher, writer],
    tasks = [research_task, write_task]
)

result = crew.kickoff(
    inputs = {"topic": topic}
)
Vamos adaptar o projeto acima para pesquisar e redigir uma notícia com dados recentes sobre as queimadas em Mato Grosso.

Faça uma cópia do arquivo main.py para agente.py

Obs. Altere os prompts, de modo com que o resultado produzido seja em Porguês do Brasil, contudo, mantenha os roles definidos para os agentes ou verifique com mais cuidado a documentação em crewAI Agents - crewAI.

Renomei também o output_file = "news.md".

Ok. Quando finalizar suba tudo para seu Git OK!

Instalar o Langflow localmente
Cuidado

O Langflow  requer que  o Python versão 3.10 ou superior e  o pip  ou  pipx  estejam instalados no seu sistema.

Instale o Langflow com pip:

  1  python -m pip install langflow -U           

Instale o Langflow com pipx:

  1  pipx install langflow --python python3.10 --fetch-missing-python           

O Pipx pode buscar a versão Python faltante para você com  --fetch-missing-python, mas você também pode instalar a versão Python manualmente. Use  --force-reinstall para garantir que você tenha a versão mais recente do Langflow e suas dependências.

⛓️ Execute o Langflow
Para executar o Langflow, digite o seguinte comando.
  1  python -m langflow run           

Confirme se uma instância local do Langflow é iniciada visitando  o site http://127.0.0.1:7860 em um navegador baseado em Chromium.


Exemplos de Fluxos no LANGFLOW
TEP - Chat com Memória

TEP - CrewAI

TEP - PDF RAG

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/Captura%20de%20tela%202024-09-12%20215701.jpg)

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/datastax.jpg)

[Ver o arquivo git.txt](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/git.txt)

[Ver o arquivo Chat com Memória.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/Chat%20com%20memoria.json)

# Aula 6
Chatbots com base de conhecimento - Dify

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/1.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/2.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/3.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/4.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/5.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/6.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/7.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/8.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/9.jpg)

[Ver o arquivo RAG documents.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/RAG%20documents.json)

[Ver o arquivo DataStax.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/datastax%20aula%2006.json)

# Aula 7
**Docker**
Docker é uma plataforma open source que possibilita o empacotamento de uma aplicação dentro de um container. Uma aplicação consegue se adequar e rodar em qualquer máquina que tenha essa tecnologia instalada.

Porque usar WSL 2 + Docker para desenvolvimento
Configurar ambientes de desenvolvimento no Windows sempre foi burocrático e complexo, além do desempenho de algumas ferramentas não serem totalmente satisfatórias.

Com o nascimento do Docker este cenário melhorou bastante, pois podemos montar nosso ambiente de desenvolvimento baseado em Unix, de forma independente e rápida, e ainda unificada com outros sistemas operacionais.

Modos de usar Docker no Windows
Docker Desktop com WSL2
Roda em cima do Virtual Machine Platform que é um componente do Hyper-V e se integra com o WSL2 permitindo rodar o Docker dentro do ambiente do Linux.

Não é necessário adquirir licença PRO do Windows 10/11.

Tem um grande desempenho e consome menos recursos quando comparado ao Docker Toolbox ou Docker Desktop com Hyper-V.

Algumas Vantagens
Tem uma ferramenta visual para administrar o Docker.
Permite instalar extensões para usar ferramentas diretas no Docker.
Permite rodar um cluster Kubernetes localmente de forma fácil.
Simplifica a configuração do Docker tanto no Windows quanto no WSL 2.
Algumas Desvantagens
Uso de memória inicial sem rodar nenhum container Docker é de 1GB ou mais.
Pode ser necessário reiniciar o Docker Desktop para que ele funcione corretamente em algumas situações.
Tende a consumir mais recursos da máquina que o Docker Engine diretamente instalado no WSL 2.
Docker Engine (Docker Nativo) diretamente instalado no WSL2
O Docker Engine é o Docker nativo (como foi criado) que roda no ambiente Linux e completamente suportado para WSL 2. Sua instalação é idêntica a descrita para as próprias distribuições Linux disponibilizadas no site do Docker.

É a maneira pura de usar o Docker no Linux.

Algumas Vantagens
Consume menos memória para rodar o Docker Daemon (servidor do Docker) quando comparado ao Docker Desktop.

Traz a experiência mais pura de usar o Docker no Linux.

Algumas Desvantagens
Se necessitar executar o Docker em outra instância do WSL 2, é necessário instalar novamente o Docker nesta instância ou configurar o acesso ao socket do Docker desejado para compartilhar o Docker entre as instâncias.

**2 - Instalar o Docker com Docker Engine (Docker Nativo)**
A instalação do Docker no WSL 2 é idêntica a instalação do Docker em sua própria distribuição Linux, portanto se você tem o Ubuntu é igual ao Ubuntu, se é Fedora é igual ao Fedora. A documentação de instalação do Docker no Linux por distribuição está aqui, mas vamos ver como instalar no Ubuntu.

![[Pasted image 20240822100956.png]]

O que o WSL 2 pode usar de recursos da sua máquina
Podemos dizer que o WSL 2 tem acesso quase que total ao recursos de sua máquina. Ele tem acesso por padrão:

A 1TB de disco rígido. É criado um disco virtual de 1TB para armazenar os arquivos do Linux (este limite pode ser expandido, ver a área de dicas e truques).
A usar completamente os recursos de processamento.
A usar 50% da memória RAM disponível.
A usar 25% da memória disponível para SWAP (memória virtual).
Se você quiser personalizar estes limites, crie um arquivo chamado .wslconfig na raiz da sua pasta de usuário (C:\Users\<seu_usuario>) e defina estas configurações:

[wsl2]
memory=8GB
processors=4
Instalando Docker
https://docs.docker.com/engine/install/ubuntu/

Install using the apt repository
Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

Set up Docker's apt repository.

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
Install the Docker packages.

Latest Specific version
To install the latest version, run:

$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Verify that the Docker Engine installation is successful by running the hello-world image.

$ sudo docker run hello-world
Fazer Ate aqui

https://github.com/codeedu/wsl2-docker-quickstart
https://learn.microsoft.com/pt-br/windows/terminal/install

**Passo 3: Inicialize os recursos do Docker**
Agora que você tem uma aplicação, podemos iniciar o processo de containerização. Dentro do diretório 'docker-nodejs-sample', execute o comando 'docker init' em um terminal e siga as instruções:

Crie um Dockerfile
Crie um arquivo chamado Dockerfile na pasta principal do seu projeto. Este arquivo irá conter as instruções para construir a imagem Docker do seu projeto.

# Use uma imagem base oficial do Node.js
FROM node:14

# Defina o diretório de trabalho dentro do container
WORKDIR /usr/src/app

# Copie o arquivo package.json e package-lock.json (se existir)
COPY package*.json ./

# Instale as dependências do projeto
RUN npm install

# Copie o restante do código do projeto
COPY . .

# Exponha a porta que o aplicativo Node.js estará escutando
EXPOSE 3000

# Comando para rodar o aplicativo
CMD ["node", "src/index.js"]
Crie um arquivo .dockerignore
node_modules
npm-debug.log
Dockerfile
.dockerignore
Construa a Imagem Docker
No terminal, navegue até a pasta principal do seu projeto e execute o seguinte comando para construir a imagem Docker:

docker images
docker build -t meu-app-node .
Execute o Container:
Após a construção da imagem, você pode executar um container a partir dela com o seguinte comando:

docker images
docker run -p 3000:3000 meu-app
docker run -p 3000:3000 -d meu-app
docker ps
docker stop
docker rm CONTAINERID
docker rmi -f meu-app
Isso mapeará a porta 3000 do container para a porta 3000 do seu host, permitindo que você acesse o aplicativo Node.js em http://localhost:3000

Utilizando o Docker compose
Utilizar o Docker Compose é uma ótima maneira de gerenciar múltiplos containers Docker de forma orquestrada, especialmente útil para aplicativos que dependem de vários serviços, como bancos de dados, servidores de cache, etc. Aqui estão os passos para configurar e usar o Docker Compose com seu projeto Node.js:

Certifique-se de que o Docker Compose está instalado no seu sistema. Você pode verificar isso com o comando:

docker compose version
Crie um arquivo docker-compose.yml:

version: '3'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
    environment:
      - NODE_ENV=production
Construa e Execute os Serviços:
No terminal, navegue até a pasta principal do seu projeto e execute o seguinte comando para construir e iniciar os serviços definidos no docker-compose.yml:

docker compose up --build
Verifique os Serviços:

docker compose ps
#parar serviço
docker compose down
Use docker-compose up -d quando quiser iniciar os serviços usando as imagens já construídas, sem reconstruir as imagens.

Use docker-compose up --build -d quando quiser garantir que as imagens sejam reconstruídas antes de iniciar os serviços, o que é útil após fazer alterações no código-fonte ou no Dockerfile.

Exemplo de um arquivo com dois serviços
version: '3'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
    environment:
      - NODE_ENV=production

  db:
    image: mysql:8
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=mysecretpassword
      - MYSQL_DATABASE=mydatabase
      - MYSQL_USER=myuser
      - MYSQL_PASSWORD=mypassword
As variáveis de ambiente correspondem às necessidades do MySQL:

MYSQL_ROOT_PASSWORD: Define a senha do usuário root.

MYSQL_DATABASE: Define o nome do banco de dados que será criado.

MYSQL_USER: Define o nome de um usuário não-root que será criado.

MYSQL_PASSWORD: Define a senha para o usuário não-root.

Referência:
https://blog.rocketseat.com.br/containerizando-uma-aplicacao-node-js-com-docker-um-guia-passo-a-passo/

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/1.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/2.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/3.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/4.jpg)

[Ver o arquivo RAG documents.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/RAG%20Documentos.json)

[Ver o arquivo CrewAI.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/TEP_-_CrewAI.json)


# Aula 8
## FLuxo - Revenda

### Formato de Resposta do Modelo - Json Schema

```json
{
  "name": "carro_escolha",
  "schema": {
    "type": "object",
    "properties": {
      "nome": {
        "type": "string",
        "description": "o nome da pessoa"
      },
      "carro": {
        "type": "string",
        "description": "o carro que o usuário escolheu, se não souber marque \"\""
      },
      "response": {
        "type": "string",
        "description": "Sua resposta para o usuário"
      },
      "etapa": {
        "type": "integer",
        "description": "o número da etapa em que você se encontra com descrito nas tags"
      }
    }
  }
}
```

Prompt LLM 1

```xml
<contexto>
Seu nome é Clara, você trabalha na Concecionaria Auto Carros.
No inicio da conversa, envie sempre a logo da loja, no formato markdown:

!["Auto Carros"](https://www.veiculoaqui.com.br/fotos_lojas/loja20231122131932721_535130177.jpeg)


Você deve orientar o usuário a encontrar o carro ideal.
</contexto>

<etapas>
1. Solicite o nome do usuário
2. Pergunte para que tipo de uso será o carro
3. Faça poucas perguntas para identificar o carro ideal para o cliente
4. Sugira um carro ou uma lista de carros com base no perfil dele
5. Assim que o usuário escolher o carro, agradeça e diga que irá encaminhá-lo para o Gerente Caetano, que irá agendar um teste Drive.
</etapas> 

<response_format>
Responda no formato JSON com os seguintes campos:
response - Sua resposta para o usuário
carro - o carro que o usuário escolheu, se não souber marque ""
nome - o nome do usuário, se não souber, marque ""
etapa - o número da etapa em que você se encontra com descrito nas tags <etapas>

</response_format>
```

Prompt LLM 2

```xml
<contexto>
Seu nome é Caetano e você é responsável por agendar o teste drive com o cliente em nossa concessionária.
</contexto>

<etapas>
1. Pergunte o endereço do usuário
2. Sugira os próximos dois dias para agendamento, hoje é {{ data_atual }}, {{ dia_da_semana }}.
3. Sugira dois horários, um de manhã e outro de tarde.
4. Agradeça ao usuário e diga que irá aguardá-lo.

</etapas>
```

Código: Pegar a data atual

```python
from datetime import datetime
def main() -> dict:
    # Dicionário para mapear os dias da semana em português
    days_of_week = {
        0: "Segunda-feira",
        1: "Terça-feira",
        2: "Quarta-feira",
        3: "Quinta-feira",
        4: "Sexta-feira",
        5: "Sábado",
        6: "Domingo"
    }

    # Obtém a data atual
    current_date = datetime.now()

    # Formata a data no formato dd/mm/aaaa
    formatted_date = current_date.strftime("%d/%m/%Y")

    # Obtém o dia da semana em português
    day_of_week = days_of_week[current_date.weekday()]

    # Retorna a data e o dia da semana
    return {
        "data_atual": formatted_date,
        "dia_da_semana": day_of_week
    }
```

2024-10-11T08:00:00.000Z

2024-10-14T08:00:00.000Z

2024-10-14T09:00:00.000Z

2024-10-14T10:00:00.000Z

# Aula 9


Implementação de chatbot/Agent no Dify
Uso de ferramentas para acessar a API do Cal.com

```xml
<Agent>
  <contexto>
  Na Clínica Médica Saúde Total, oferecemos serviços completos de fisioterapia voltados à recuperação e ao bem-estar dos nossos pacientes. O Dr. Benevid Felix da Silva, especialista na área, está à disposição para proporcionar tratamentos personalizados, incluindo:

Reabilitação Muscular e Articular: Tratamentos para alívio de dores e recuperação de movimentos em lesões, pós-operatórios e condições crônicas.
Terapias Preventivas: Fisioterapia preventiva para fortalecer músculos, melhorar a postura e evitar futuras lesões.
Tratamento de Condições Neuromusculares: Reabilitação focada em pacientes com doenças neurológicas, como AVC, esclerose múltipla e Parkinson.
Fisioterapia Ortopédica: Cuidados especializados para recuperação de fraturas, torções e problemas ortopédicos.
Nosso objetivo é melhorar a qualidade de vida dos pacientes por meio de tratamentos eficazes e personalizados.
  </contexto>
  
  
  
    <Description>
        O agente virtual da Clínica Médica Saúde Total é projetado para ajudar pacientes com agendamentos de consultas, fornecimento de informações sobre serviços médicos, esclarecimento de dúvidas e gerenciamento de registros de pacientes.
    </Description>

    <Language>pt-BR</Language>

<Hour>
Utilize como padrão o fuso horário GMT -4, descontando e atualizando a hora fornecida pela ferramenta current_time, que está em GMT 0.  Não dê informações sobre o fuso, apenas informe horas. 
</Hour>

<weekday>
Utilize o GMT -4 para informar o dia da semana, considerando que a ferramenta current_time está em GMT 0. Faça os cálculos de horas a menos para informar o dia correto.
</weekday>
 
<CommunicationStyle>
        <Tone>Calmo e acolhedor</Tone>
        <Formality>Formal</Formality>
</CommunicationStyle>
    
<etapas>
1. Solicite o nome da pessoa, email e telefone. Esses dados são necessários para fazer o agendamento da consulta.
2. Pergunte para que dia deseja agendar a consulta.
3. Faça poucas perguntas para identificar os dados junto ao cliente
4. Sugira uma data com base na lista de slots vagos. Os slots vagos para agendamento podem ser consultados utilizando a ferramenta get_slots_cal_com.
5. Assim que o usuário escolher o horário, faça o agendamento utilizando a ferramenta criar_agendamento_cal_com. Confirme o agendamento com a ferramenta get_bookings_cal_com.
6.Ao confirmar o agendamento
</etapas> 


</Agent>
```


## Definição dos temas dos trabalhos

🚀 Proposta de Tema para Trabalho de Tópicos Especiais em Programação 🚀

## 📝 Informações Básicas

- **Nome do Aluno(s):** [Nome do Aluno 1], [Nome do Aluno 2], ...

## 🎯 Tema Proposto

### 📌 Título do Projeto

[Insira o título do projeto aqui]

### 📌 Descrição do Projeto

[Descreva o tema proposto de forma clara e concisa. Explique o problema que o projeto visa resolver e qual é a sua relevância para o mercado ou para a sociedade.]

### 📌 Objetivos

[Liste os objetivos principais do projeto. Por exemplo, automatizar um processo específico, melhorar a eficiência de um sistema, etc.]

### 📌 Ferramentas e Tecnologias Sugeridas

[Liste as ferramentas e tecnologias que vocês planejam utilizar para desenvolver o projeto. Exemplos: LLM, RAG, Langchain, Dify, N8N, etc.]

### 📌 Funcionalidades Principais

[Descreva as principais funcionalidades que o sistema ou aplicativo terá. Use uma lista para facilitar a visualização.]

- Funcionalidade 1: [Descrição da funcionalidade 1]
- Funcionalidade 2: [Descrição da funcionalidade 2]
- Funcionalidade 3: [Descrição da funcionalidade 3]
- ...

### 📌 Atividades por Membro da Equipe

[Especifique as atividades que cada membro da equipe irá desenvolver. Isso ajuda a garantir que todas as partes do projeto sejam cobertas.]

- **[Nome do Aluno 1]:** [Atividade 1], [Atividade 2], ...
- **[Nome do Aluno 2]:** [Atividade 1], [Atividade 2], ...
- ...

### 📌 Cronograma Preliminar

[Proponha um cronograma preliminar para o desenvolvimento do projeto. Use uma tabela para listar as principais etapas e prazos.]

| Etapa | Descrição              | Prazo  | Responsável(eis)   |
| ----- | ---------------------- | ------ | ------------------ |
| 1     | [Descrição da Etapa 1] | [Data] | [Nome do Aluno(s)] |
| 2     | [Descrição da Etapa 2] | [Data] | [Nome do Aluno(s)] |
| ...   | ...                    | ...    | ...                |

### 📌 Referências

[Liste as principais referências que vocês utilizarão para desenvolver o projeto. Isso pode incluir artigos, documentações de APIs, tutoriais, etc.]

- Referência 1: [Descrição da Referência 1]
- Referência 2: [Descrição da Referência 2]
- ...

## 📬 Envio da Proposta

Enviar através do SIGAA, na Tarefa correspondente. Caso tenha dúvidas, encaminhe via whatsapp professor antes de submeter a tarefa.

---

**Observação:** Certifique-se de que a proposta esteja clara, detalhada e coerente com os objetivos do trabalho de Tópicos Especiais em Programação. A equipe avaliará a viabilidade e a relevância do tema proposto.

# Aula 10

Instalação do N8n


## APIS do WhatsApp
### go-whatsapp-web-multidevice

- Send WhatsApp message via http API, 
- [docs/openapi.yml](https://github.com/aldinokemal/go-whatsapp-web-multidevice/blob/main/docs/openapi.yaml) for more details
- Compress image before send
- Compress video before send

Arquivo: docker-compose.yaml

```bash
version: '3.9'
services:
  whatsapp_go:
    logging:
      driver: "json-file"
      options:
        max-size: "200k"
        max-file: "10"
    image: "aldinokemal2104/go-whatsapp-web-multidevice:latest"
    build:
      context: .
      dockerfile: ./docker/golang.Dockerfile
    restart: 'always'
    ports:
      - "3100:3000"
    environment:
      - WEBHOOK="https://n8n.semcodigo.edu.pl/webhook-test/consultavendas"
    volumes:
      - whatsapp_data:/app/storages

volumes:
  whatsapp_data:
```




```bash
sudo docker run --detach --publish=3001:3000 --name=whatsapp2 --restart=always --volume=$(sudo docker volume create --name=whatsapp2):/app/storages aldinokemal2104/go-whatsapp-web-multidevice --autoreply="Don't reply this message please" --webhook="http://localhost:5678/webhook-test/whats"
```


### Evolution


A Evolution API v2 está pronta para o Docker e pode ser facilmente implantada com Docker no modo standalone ou swarm. O repositório oficial do Evolution API contém todos os arquivos de composição necessários para instalar e executar a API.

Originalmente, a **Evolution API** começou como uma API de controle de WhatsApp baseada no CodeChat, utilizando a biblioteca Baileys. Com o tempo, a plataforma se expandiu para suportar não apenas o WhatsApp, mas também integrações com serviços como **Typebot, Chatwoot, Dify e OpenAI**. Além disso, a Evolution API suporta tanto a API de WhatsApp baseada no Baileys quanto a API oficial do WhatsApp Business, com suporte futuro planejado para Instagram e Messenger.

Processo de Instalação: 
- https://doc.evolution-api.com/v2/pt/install/docker


O banco de dados é uma parte fundamental da Evolution API v2, responsável por armazenar todas as informações críticas da aplicação. A API suporta tanto PostgreSQL quanto MySQL, utilizando o Prisma como ORM (Object-Relational Mapping) para facilitar a interação com esses bancos de dados.

A maneira mais fácil e rápida de configurar um banco de dados para a Evolution API v2 é através do Docker. Abaixo estão as instruções para configurar tanto o PostgreSQL quanto o MySQL usando Docker Compose.

##### Instalação do Postgres

Para configurar o PostgreSQL via Docker, siga os passos abaixo:

1. Baixe o arquivo `docker-compose.yaml` para o PostgreSQL disponível [aqui](https://github.com/EvolutionAPI/evolution-api/blob/v2.0.0/Docker/postgres/docker-compose.yaml).

```bash
version: '3.3'

services:
  postgres:
    container_name: postgres
    image: postgres:15
    networks:
      - evolution-net
    command: ["postgres", "-c", "max_connections=1000"]
    restart: always
    ports:
      - 5432:5432
    environment:
      - POSTGRES_PASSWORD=PASSWORD
    volumes:
      - postgres_data:/var/lib/postgresql/data
    expose:
      - 5432

  pgadmin:
    image: dpage/pgadmin4:latest
    networks:
      - evolution-net
    environment:
      - PGADMIN_DEFAULT_EMAIL=EMAIL
      - PGADMIN_DEFAULT_PASSWORD=PASSWORD  
    volumes:
      - pgadmin_data:/var/lib/pgadmin
    ports:
      - 4000:80
    links:
      - postgres

volumes:
  postgres_data:
  pgadmin_data:


networks:
  evolution-net:
    name: evolution-net
    driver: bridge
```


No meu caso, com base nas listas de redes disponíveis no docker - já com outras ferramentas instanciadas, como n8n, Dify e Langflow tive que **alterar a porta e também a subrede**.

```bash
version: '3.3'

services:
postgres:
    container_name: postgres
    image: postgres:15
    networks:
      - evolution-net
    command: ["postgres", "-c", "max_connections=1000"]
    restart: always
    ports:
      - 5433:5432  # Mapeia a porta 5433 no host para a porta 5432 no contêiner
    environment:
      - POSTGRES_PASSWORD=8H4a10032024
    volumes:
      - postgres_data:/var/lib/postgresql/data
    expose:
      - 5432  # Mantém a porta 5432 para exposição interna

  pgadmin:
    image: dpage/pgadmin4:latest
    networks:
      - evolution-net
    environment:
      - PGADMIN_DEFAULT_EMAIL=benevid@unemat.br
      - PGADMIN_DEFAULT_PASSWORD=8H4a10032024  
    volumes:
      - pgadmin_data:/var/lib/pgadmin
    ports:
      - 4000:80
    links:
      - postgres

volumes:
  postgres_data:
  pgadmin_data:


networks:
  evolution-net:
    name: evolution-net
    driver: bridge
    ipam:
      config:
        - subnet: 172.22.0.0/16
```

No meu caso tive que rodar o seguinte comando para criar o banco de dados:

```bash
docker-compose up -d
docker exec -it postgres psql -U postgres -c "CREATE DATABASE evolution;"
```

Variáveis de ambiente para habilitar no `.env`

```bash
# Habilitar o uso do banco de dados
DATABASE_ENABLED=true

# Escolher o provedor do banco de dados: postgresql ou mysql
DATABASE_PROVIDER=postgresql

# URI de conexão com o banco de dados
DATABASE_CONNECTION_URI='postgresql://user:pass@localhost:5432/evolution?schema=public'

# Nome do cliente para a conexão do banco de dados
DATABASE_CONNECTION_CLIENT_NAME=evolution_exchange

# Escolha os dados que você deseja salvar no banco de dados da aplicação
DATABASE_SAVE_DATA_INSTANCE=true
DATABASE_SAVE_DATA_NEW_MESSAGE=true
DATABASE_SAVE_MESSAGE_UPDATE=true
DATABASE_SAVE_DATA_CONTACTS=true
DATABASE_SAVE_DATA_CHATS=true
DATABASE_SAVE_DATA_LABELS=true
DATABASE_SAVE_DATA_HISTORIC=true

```


### Instalação do Redis
O Redis é utilizado pela Evolution API v2 como um sistema de cache para otimizar o desempenho e a velocidade da aplicação. Ele pode ser configurado para armazenar informações temporárias e melhorar a eficiência das operações.

Para configurar o Redis via Docker, siga os passos abaixo:

1. Baixe o arquivo `docker-compose.yaml` para o Redis disponível [aqui](https://github.com/EvolutionAPI/evolution-api/blob/v2.0.0/Docker/redis/docker-compose.yaml).
2. Navegue até o diretório onde o arquivo foi baixado e execute o comando:

```bash
docker-compose up -d
```

```bash
version: '3.3'

services:
  redis:
    image: redis:latest
    container_name: redis
    command: >
      redis-server --port 6379 --appendonly yes
    volumes:
      - evolution_redis:/data
    ports:
      - 6380:6379

volumes:
  evolution_redis:

networks:
  evolution-net:
    name: evolution-net
    driver: bridge
```


Variáveis de ambiente para habilitar no `.env`

```bash
# Habilitar o cache Redis
CACHE_REDIS_ENABLED=true

# URI de conexão com o Redis
CACHE_REDIS_URI=redis://localhost:6379/6

# Prefixo para diferenciar os dados de diferentes instalações que utilizam o mesmo Redis
CACHE_REDIS_PREFIX_KEY=evolution

# Habilitar para salvar as informações de conexão no Redis ao invés do banco de dados
CACHE_REDIS_SAVE_INSTANCES=false

# Habilitar o cache local
CACHE_LOCAL_ENABLED=false
```


**Instalação da Evolution**


```bash
version: '3.9'
services:
  evolution-api:
    container_name: evolution_api
    image: atendai/evolution-api:v2.1.1
    restart: always
    ports:
      - "8080:8080"
    env_file:
      - .env
    volumes:
      - evolution_instances:/evolution/instances

volumes:
  evolution_instances:

```

No meu tive que mudar a porta de saída porque dava choque com outra ferramenta. Ficando assim:

```bash
version: '3.9'
services:
  evolution-api:
    container_name: evolution_api
    image: atendai/evolution-api:v2.0.9-rc
    restart: always
    ports:
      - "8081:8080" # Mapeia 8081 (host) p/ 8080 (contêiner)
    env_file:
      - .env
    volumes:
      - evolution_instances:/evolution/instances

volumes:
  evolution_instances:
```

Em seguida, crie um arquivo `.env` no mesmo diretório com o seguinte conteúdo mínimo:

```bash
AUTHENTICATION_API_KEY=mude-me
```


Arquivo final do `.env`

```bash
## ------------------- BANCO DE DADOS -----------------------
# Habilitar o uso do banco de dados
DATABASE_ENABLED=true

# Escolher o provedor do banco de dados: postgresql ou mysql
DATABASE_PROVIDER=postgresql

# URI de conexão com o banco de dados
DATABASE_CONNECTION_URI='postgresql://postgres:8H4a10032024@5.78.105.1:5433/evolution?schema=public'
# Nome do cliente para a conexão do banco de dados
DATABASE_CONNECTION_CLIENT_NAME=evolution_exchange

# Escolha os dados que você deseja salvar no banco de dados da aplicação
DATABASE_SAVE_DATA_INSTANCE=true
DATABASE_SAVE_DATA_NEW_MESSAGE=true
DATABASE_SAVE_MESSAGE_UPDATE=true
DATABASE_SAVE_DATA_CONTACTS=true
DATABASE_SAVE_DATA_CHATS=true
DATABASE_SAVE_DATA_LABELS=true
DATABASE_SAVE_DATA_HISTORIC=true

## ----------------------- REDIS -------------------

# Habilitar o cache Redis
CACHE_REDIS_ENABLED=true

# URI de conexão com o Redis
CACHE_REDIS_URI=redis://5.78.105.1:6380/6

# Prefixo para diferenciar os dados de diferentes instalações que utilizam o mesmo Redis
CACHE_REDIS_PREFIX_KEY=evolution

# Habilitar para salvar as informações de conexão no Redis ao invés do banco de dados
CACHE_REDIS_SAVE_INSTANCES=false

# Habilitar o cache local
CACHE_LOCAL_ENABLED=false

AUTHENTICATION_API_KEY=bccb5913-0ba2-41e9-b67c-05dca0be1791
```


Iniciar o evolution

```bash
docker compose up -d
docker logs evolution_api
```



```json
{ "slots": { "2024-10-28": [ { "time": "2024-10-28T12:00:00.000Z" }, { "time": "2024-10-28T13:00:00.000Z" }, { "time": "2024-10-28T14:00:00.000Z" }, { "time": "2024-10-28T15:00:00.000Z" }, { "time": "2024-10-28T16:00:00.000Z" }, { "time": "2024-10-28T17:00:00.000Z" }, { "time": "2024-10-28T18:00:00.000Z" }, { "time": "2024-10-28T19:00:00.000Z" }, { "time": "2024-10-28T20:00:00.000Z" } ], "2024-10-29": [ { "time": "2024-10-29T17:00:00.000Z" }, { "time": "2024-10-29T18:00:00.000Z" }, { "time": "2024-10-29T19:00:00.000Z" }, { "time": "2024-10-29T20:00:00.000Z" } ], "2024-10-30": [ { "time": "2024-10-30T12:00:00.000Z" }, { "time": "2024-10-30T13:00:00.000Z" }, { "time": "2024-10-30T14:00:00.000Z" }, { "time": "2024-10-30T15:00:00.000Z" }, { "time": "2024-10-30T16:00:00.000Z" }, { "time": "2024-10-30T17:00:00.000Z" }, { "time": "2024-10-30T18:00:00.000Z" }, { "time": "2024-10-30T19:00:00.000Z" }, { "time": "2024-10-30T20:00:00.000Z" } ] } }
```

