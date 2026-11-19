# Estado do projeto e ponto de retomada

Atualizado em **19 de novembro de 2026**.

## Objetivo

Estudar **relaxação, equilibração e termalização em mecânica quântica**,
tendo o modelo de Hubbard como modelo-alvo. O usuário vem de mecânica
estatística e fenômenos críticos e já conhece mecânica quântica e operadores
de criação e aniquilação. O percurso deve servir à entrada em uma nova área
de pesquisa, conectando conceitos, cálculos e, posteriormente, simulações.

## Decisões tomadas

- Começar com uma **cadeia de spins como laboratório conceitual** e depois
  retornar ao Hubbard, incorporando a dinâmica de carga.
- Trabalhar provisoriamente com **sistemas fechados e evolução unitária**.
  Sistemas abertos não estão excluídos, mas não são o foco inicial.
- Não usar o dímero como principal exemplo de termalização: ele foi
  discutido como exercício de base de Fock, sinais e dinâmica local, mas
  suas oscilações e recorrências limitam esse propósito.
- Distinguir sempre relaxação, equilibração e termalização. Um patamar
  temporal não demonstra, por si só, compatibilidade com um ensemble térmico.
- Comparar tamanhos e janelas temporais; não extrapolar automaticamente
  observações finitas para o limite termodinâmico.

## Proposta de trabalho registrada no roteiro

1. Cadeia aberta de spins `1/2`, com número par de sítios, trocas `J1 > 0`
   entre primeiros vizinhos e `J2` entre segundos vizinhos.
2. Preparação inicial sugerida: estado produto de Néel.
3. Acompanhar magnetização alternada e correlações por ligação. A
   magnetização total conservada serve como controle, não como sinal de
   relaxação; para `J2 = 0`, a soma das correlações de primeiros vizinhos
   também está vinculada à energia conservada.
4. Comparar o caso integrável `J2 = 0` com valores genéricos de `J2` que
   quebrem a integrabilidade, sem pressupor termalização ou relaxação rápida.
5. Examinar médias, flutuações e referências estacionárias antes da
   comparação com previsões térmicas. Considerar conservações adicionais
   e ensembles generalizados quando pertinentes.
6. Retornar ao Hubbard para estudar também dupla ocupação e, em preparações
   apropriadas, desequilíbrio de densidade.

**Ressalvas físicas:** a cadeia uniforme de Hubbard com hopping apenas entre
primeiros vizinhos também é integrável. A ponte Hubbard–Heisenberg,
com `J = 4t²/U`, exige Hubbard repulsivo, meio preenchimento, acoplamento forte
e o subespaço de baixa energia apropriado; não descreve quenches arbitrários
com excitações apreciáveis de carga. O termo `J2` é uma comparação dinâmica,
não a troca efetiva dominante do Hubbard de primeiros vizinhos.

## Material existente

- [Roteiro em LaTeX](notas/roteiro_equilibracao_hubbard.tex):
  documento principal, intitulado *Equilibração e termalização: das cadeias
  de spins ao modelo de Hubbard*. Contém modelos, convenções, observáveis,
  protocolo sugerido e critérios de progresso.
- `notas/roteiro_equilibracao_hubbard.pdf`: PDF presente na árvore de
  trabalho, com cinco páginas; também existem arquivos auxiliares de LaTeX.
- [AGENTS.md](AGENTS.md): convenções físicas, regras de colaboração e de
  reprodutibilidade. Consultar antes de dar continuidade.
- `.opencode/agents/` e `opencode.json`: configuração da equipe.

O caminho do documento foi simplificado por pedido explícito do usuário:
**usar `notas/roteiro_equilibracao_hubbard.tex`, não `notas/aulas/`.**
O roteiro é um registro inicial, não uma revisão bibliográfica ou um relato
de resultados.

## Verificações e limites do que foi feito

- O fonte foi revisado e compilado com `pdflatex` em duas passagens durante
  sua elaboração, em diretório temporário, gerando um PDF de cinco páginas.
- O log atualmente presente em `notas/` registra uma compilação com avisos
  de referências pendentes e pedido de nova passagem. Para atualizar esse
  PDF, executar `pdflatex` duas vezes sobre o fonte no caminho atual.
- Há também avisos de configuração do `babel` sobre o nome `brazil` e
  padrões de hifenização; não impediram a geração do PDF.
- **Não há implementação científica, simulações, resultados numéricos ou
  testes Julia executados.** Compilar o documento não valida dinâmica física.
- Não foram instaladas dependências nem escolhido um algoritmo numérico.

## Próximo passo recomendado

Retomar a partir do roteiro, começando pela **formulação do problema dinâmico
na cadeia de spins**: Hamiltoniano, estado de Néel, quantidades conservadas
e significado dos observáveis. Não retomar automaticamente a sequência do
dímero como se a mudança de foco não tivesse ocorrido.

Antes de implementar:

- Incorporar o roteiro pessoal do usuário, que foi mencionado, mas ainda
  não foi compartilhado.
- Confirmar ou ajustar o protocolo e o foco provisório em sistemas fechados.
- Escolher parâmetros, tamanhos, janelas temporais, tolerâncias e referências
  térmicas/estacionárias; esses valores ainda não estão definidos.
- Definir método em Julia somente após estimar dimensão dos setores,
  memória e custo. Não iniciar cálculos extensos ou instalar pacotes sem
  autorização compatível.
- Selecionar bibliografia verificável; ainda não foi produzida uma lista.

### Sugestão de mensagem para retomar

> Leia AGENTS.md, STATUS.md e notas/roteiro_equilibracao_hubbard.tex.
> Vamos retomar o estudo de equilibração pela cadeia de spins, começando
> pelo Hamiltoniano, pela preparação de Néel e pelos observáveis, ainda
> sem implementar simulações.

O material a versionar é o fonte LaTeX, este registro, o README e as
configurações do projeto. O PDF, os arquivos auxiliares de compilação e
o backup `README.md.pre-hubbard` são artefatos locais, não necessários
para retomar o estudo a partir dos fontes.
