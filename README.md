# Estudo do modelo de Hubbard

Projeto para estudar o modelo de Hubbard com um **orquestrador**, quatro especialistas recrutados sob demanda e implementação dos métodos numéricos em **Julia**.

## Estado do estudo e retomada

O foco atual é **relaxação, equilibração e termalização**, começando com
cadeias de spins como preparação para a dinâmica no modelo de Hubbard.

- [Status, decisões e próximos passos](STATUS.md).
- [Roteiro de estudos em LaTeX](notas/roteiro_equilibracao_hubbard.tex).

Para retomar o trabalho, consulte `AGENTS.md`, `STATUS.md` e o roteiro acima.

## Equipe de agentes

| Agente | Papel |
| --- | --- |
| `orquestrador` | Agente principal: entender o pedido, organizar o trabalho, recrutar especialistas e integrar as entregas. |
| `fisico-teorico` | Formular o problema, desenvolver derivações e revisar hipóteses e limites físicos. |
| `professor` | Explicar os conceitos passo a passo e propor exemplos e exercícios. |
| `redator` | Organizar e revisar a escrita científica sem alterar o significado dos resultados. |
| `fisico-computacional` | Implementar algoritmos em Julia e validar os resultados numéricos. |

As definições ficam em `.opencode/agents/`. O arquivo `AGENTS.md` contém as convenções físicas e as regras comuns.

## Como usar no OpenCode

Converse com o **`orquestrador`**, configurado com `mode: primary` e como padrão do projeto em `opencode.json`. Os quatro especialistas usam `mode: subagent` e são chamados somente quando a tarefa precisar deles. Não há modelo de IA fixado nos arquivos; em delegações, os especialistas herdam o modelo da sessão que os chamou.

Você não precisa escolher os especialistas manualmente. Por exemplo:

```text
Quero entender o dímero de Hubbard e depois verificar seu espectro em Julia.
Organize o estudo e chame os especialistas necessários.
```

O orquestrador pode responder diretamente a questões simples. Para esse estudo, pode recrutar o teórico, o professor e o computacional; o redator só será necessário se houver uma entrega de escrita.

Se preferir, você também pode pedir uma delegação específica:

```text
Use o agente fisico-teorico para derivar o espectro do dímero de Hubbard
com dois elétrons. Explicite a base, os sinais e a convenção de energia.
```

```text
Use o agente professor para me explicar segunda quantização aplicada ao
modelo de Hubbard, começando pelos estados de um único sítio.
```

```text
Use o agente fisico-computacional para implementar o dímero em Julia,
com testes contra o resultado analítico. Antes de instalar pacotes, me consulte.
```

```text
Use o agente redator para transformar as notas existentes em um texto
coeso, preservando as hipóteses e sinalizando as referências pendentes.
```

Para um trabalho integrado:

```text
Coordene os quatro agentes para estudar o dímero de Hubbard:
primeiro a derivação teórica, depois a implementação e os testes em Julia,
em seguida uma explicação didática e, por fim, um texto com os resultados.
Não atribua o mesmo arquivo a dois agentes simultaneamente.
```

Os especialistas não chamam outros agentes: a coordenação fica com o orquestrador, autorizado a recrutar somente os quatro perfis do projeto. Teórico, professor e redator não têm acesso ao shell; o físico computacional pode executar comandos sujeitos às permissões do ambiente.

O OpenCode recarrega as definições dos agentes após salvar. Se precisar forçar uma atualização, use `/reload`.

**Nesta conversa já aberta**, use `/agents` e selecione `orquestrador`. A mudança do agente padrão não troca automaticamente o agente de uma sessão existente. Em novas sessões sem seleção explícita, o padrão passa a ser o orquestrador.

## Organização prevista

Os diretórios abaixo serão criados conforme surgir conteúdo, sem gerar arquivos vazios:

```text
notas/teoria/    # Derivações e convenções
notas/aulas/     # Explicações e exercícios
textos/         # Redação científica
referencias/    # Bibliografia e fichamentos
src/            # Código Julia reutilizável
scripts/        # Execução de experimentos
test/           # Testes automatizados
notebooks/      # Explorações interativas
resultados/     # Saídas com parâmetros e procedência
```

Além da configuração dos agentes e das orientações do projeto, há um roteiro
inicial em `notas/roteiro_equilibracao_hubbard.tex`. Ainda não há implementações
científicas nem resultados de simulações.
