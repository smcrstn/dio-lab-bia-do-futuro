# LogiAssist — Avaliação e testes do protótipo

## 1. Objetivo

Este documento registra os testes realizados no protótipo LogiAssist, um assistente de apoio à triagem de ocorrências logísticas. A avaliação verifica a cobertura da base de conhecimento, o tratamento de informações incompletas e o comportamento diante de categorias não cadastradas.

## 2. Escopo avaliado

A base de conhecimento está organizada em JSON e contém sete categorias:

1. Atraso na entrega
2. Rastreamento sem atualização
3. Tentativa de entrega sem sucesso
4. Divergência de status
5. Avaria ou possível extravio
6. Devolução
7. Problema com endereço

Cada categoria possui informações a verificar, ações recomendadas e restrições sobre conclusões que não devem ser feitas sem evidências.

## 3. Testes realizados

### Teste 1 — Cobertura estrutural das categorias

**Objetivo:** verificar se as sete categorias cadastradas possuem os campos necessários para orientar a triagem.

**Critérios verificados:**
- Categoria identificada;
- Lista de informações a verificar;
- Lista de ações recomendadas;
- Lista de restrições.

**Resultado:** 7 de 7 categorias apresentaram a estrutura esperada.

**Cobertura estrutural:** 100%.

### Teste 2 — Informações incompletas

**Cenário:** ocorrência de rastreamento sem atualização, sem código de rastreamento, último evento, data do último evento ou prazo previsto.

**Resultado esperado:** identificar os campos ausentes e manter a ocorrência pendente de informações, sem criar dados.

**Resultado obtido:** os quatro campos ausentes foram identificados e o sistema apresentou a mensagem: “ocorrência pendente de informações”.

**Status:** aprovado.

### Teste 3 — Categoria desconhecida

**Cenário:** entrada da categoria “Problema com pagamento”, que não está cadastrada na base de conhecimento.

**Resultado esperado:** não associar a ocorrência a uma categoria por aproximação nem inventar um procedimento; encaminhar para análise humana.

**Resultado obtido:** o sistema informou que a categoria não foi identificada na base e recomendou encaminhamento para análise humana.

**Status:** aprovado.

### Teste 4 — Geração de respostas para as sete categorias

**Objetivo:** verificar se a resposta gerada apresenta a situação correspondente à categoria, as informações a verificar, as ações recomendadas e as restrições cadastradas.

**Resultado:** foram geradas respostas para as sete categorias. A revisão do resultado mostrou que as orientações e restrições correspondiam aos registros da base de conhecimento.

**Status:** aprovado na verificação funcional realizada.

## 4. Resumo dos resultados

| Indicador | Resultado |
|---|---:|
| Categorias cadastradas | 7 |
| Categorias com estrutura válida | 7 |
| Cobertura estrutural da base | 100% |
| Teste de informações incompletas | Aprovado |
| Teste de categoria desconhecida | Aprovado |
| Geração de respostas para as categorias | 7 respostas verificadas |

## 5. Limitações identificadas

- Os testes realizados são verificações funcionais do protótipo e não representam uma avaliação estatística de precisão, acurácia ou desempenho em produção.
- Os cenários utilizados são controlados e não substituem testes com ocorrências reais anonimizadas e validadas por profissionais da operação.
- O modelo Qwen2.5-0.5B-Instruct foi experimentado como camada de linguagem, mas apresentou respostas inconsistentes em alguns cenários, incluindo conclusões sem evidência suficiente.
- Por segurança, a versão avaliada utiliza regras em Python e dados da base JSON como referência para a triagem. O modelo de linguagem não deve decidir sozinho sobre extravio, entrega, responsabilidade ou prazos.
- O protótipo não consulta rastreamento em tempo real, não altera pedidos, não abre chamados e não executa ações em sistemas de transportadoras ou marketplaces.

## 6. Conclusão

Nos cenários testados, o protótipo demonstrou capacidade de consultar a base de conhecimento, organizar orientações por categoria, identificar informações ausentes e reconhecer categorias não cadastradas.

Os resultados indicam que a estrutura inicial atende ao objetivo de demonstrar uma triagem logística assistida por regras, com limites explícitos para evitar conclusões sem evidências. Antes de qualquer uso operacional, são necessários testes ampliados, validação por especialistas e integração controlada com fontes oficiais.

## 7. Próximas melhorias

1. Ampliar a quantidade e a variedade de cenários de teste.
2. Avaliar entradas ambíguas, contraditórias e com dados parcialmente preenchidos.
3. Criar um conjunto de casos de referência revisados por profissionais de logística.
4. Medir separadamente a identificação de categoria, a detecção de dados ausentes e a conformidade das respostas.
5. Melhorar a interface de demonstração e documentar o fluxo de uso.
