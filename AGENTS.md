# Projeto: estudo do modelo de Hubbard

## Objetivo e comunicação

- Apoiar o estudo do modelo de Hubbard, da fundamentação teórica às simulações em Julia e à escrita científica.
- Responder em português brasileiro, salvo solicitação diferente. Usar LaTeX para equações.
- Não presumir o nível de formação do usuário. Quando necessário, perguntar sobre pré-requisitos e objetivo; se for possível avançar, explicitar as hipóteses adotadas.
- Distinguir resultados exatos, aproximações controladas, argumentos heurísticos e observações numéricas.
- Não inventar referências, demonstrações, dados, gráficos ou execuções de testes. Informar limitações e pendências.

## Convenções físicas

Na ausência de outra convenção explícita, usar o modelo fermiônico de uma banda:

\[
H = -t \sum_{\langle i,j\rangle,\sigma}
\left(c^\dagger_{i\sigma}c_{j\sigma}
+ c^\dagger_{j\sigma}c_{i\sigma}\right)
+ U\sum_i n_{i\uparrow}n_{i\downarrow}
- \mu\sum_{i,\sigma} n_{i\sigma}.
\]

- Cada ligação não orientada aparece uma única vez em \(\langle i,j\rangle\); o conjugado hermitiano está escrito explicitamente.
- \(t\) é o hopping real entre primeiros vizinhos, \(U\) a interação local e \(\mu\) o potencial químico; \(n_{i\sigma}=c^\dagger_{i\sigma}c_{i\sigma}\).
- Não fixar dimensão, geometria, condições de contorno, sinal de \(U\), preenchimento ou ensemble sem declarar.
- Informar número de sítios \(L\), número de partículas \(N\) e densidade \(n=N/L\), quando pertinentes. Meio preenchimento significa \(N=L\).
- Distinguir o Hamiltoniano canônico sem o termo \(-\mu N\) da formulação grand-canônica; não comparar energias de convenções diferentes sem conversão.
- Ao usar a interação deslocada \(U(n_\uparrow-1/2)(n_\downarrow-1/2)\), explicitar as mudanças no termo químico e na constante.
- Na convenção não deslocada acima, \(\mu=U/2\) é o valor de simetria partícula-buraco para o caso bipartido com hopping apenas entre sub-redes; não generalizar para redes ou hoppings arbitrários.
- Declarar unidades. Pode-se adotar \(\hbar=k_B=1\) e \(t=1\), desde que isso seja explicitado e não elimine o limite atômico \(t=0\) da análise.
- Indicar domínio de validade: por exemplo, \(J=4t^2/U\) descreve a troca antiferromagnética dominante para \(U>0\), \(U\gg |t|\), em meio preenchimento e no subespaço de baixa energia apropriado.

## Agentes e colaboração

Os perfis estão em `.opencode/agents/`:

- `orquestrador`: agente principal e ponto de contato com o usuário; planeja, recruta especialistas sob demanda e integra os resultados.
- `fisico-teorico`: formulação, derivações, simetrias, limites e revisão física.
- `professor`: explicações graduais, exemplos e exercícios.
- `redator`: organização, clareza, notação e redação científica.
- `fisico-computacional`: algoritmos, implementação e validação em Julia.

O `orquestrador` usa `mode: primary` e é o padrão do projeto em `opencode.json`. Os outros quatro perfis usam `mode: subagent`: são especialistas recrutados quando necessário, não agentes principais.

O orquestrador responde diretamente a questões simples e de organização. Para tarefas especializadas substanciais ou pedidos explícitos de trabalho em equipe, delega apenas aos perfis pertinentes. O usuário não precisa citar os nomes dos especialistas em toda solicitação.

- Enviar ao subagente uma tarefa autocontida: pergunta, convenções, arquivos relevantes, saída esperada e restrições.
- Preferir teoria → implementação → validação → explicação → redação, ajustando ao objetivo.
- Paralelizar apenas trabalhos independentes; nunca atribuir o mesmo arquivo a dois agentes ao mesmo tempo.
- Os especialistas não delegam recursivamente. O agente principal integra os resultados e resolve divergências explicitamente.
- Uma revisão teórica não substitui testes numéricos, e um teste que passa não demonstra uma afirmação física geral.
- Não implementar simulações extensas, instalar dependências ou iniciar cálculos caros sem necessidade e autorização compatíveis com o pedido.

## Organização de arquivos

Criar diretórios apenas quando houver conteúdo solicitado:

- `notas/teoria/`: derivações e convenções.
- `notas/aulas/`: material didático e exercícios.
- `textos/`: rascunhos e textos científicos.
- `referencias/`: bibliografia e fichamentos com origem verificável.
- `src/`: implementação Julia reutilizável.
- `scripts/`: execução de experimentos.
- `test/`: testes automatizados Julia.
- `notebooks/`: explorações, preferencialmente sem duplicar a implementação de `src/`.
- `resultados/`: saídas acompanhadas de parâmetros e procedência.

Preservar o trabalho existente. Não tratar os diretórios acima como autorização para criar conteúdo fora do pedido.

## Código e reprodutibilidade

- Usar Julia para os códigos científicos, salvo solicitação explícita diferente.
- Preferir `LinearAlgebra`, `SparseArrays`, `Random` e `Test` quando suficientes; justificar pacotes externos.
- Declarar a ordenação dos orbitais de spin e da base de Fock, a convenção de sinais fermiônicos e os setores de simetria.
- Estimar dimensão do espaço de Hilbert, memória e custo antes de diagonalizações; não construir matrizes densas grandes por padrão.
- Testar hermiticidade, sinais de hopping, conservação de quantidades pertinentes e limites acessíveis, como \(U=0\), \(t=0\) e sistemas pequenos.
- Registrar versão de Julia, ambiente, parâmetros, condições de contorno, tolerâncias e semente quando houver aleatoriedade.
- Quando existir um pacote Julia, usar `julia --project=. -e 'using Pkg; Pkg.test()'`; para uma suíte simples existente, usar `julia --project=. test/runtests.jl`.
- Não executar comandos de testes antes de verificar que os arquivos correspondentes existem. Informar exatamente o que foi executado e o que não foi.
- Não criar ou editar manualmente `Manifest.toml` para simular resolução de dependências; gerá-lo pelo gerenciador de pacotes quando pertinente.
