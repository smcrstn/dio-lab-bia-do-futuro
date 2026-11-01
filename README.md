# LogiAssist — Assistente Inteligente de Operações Logísticas

## Visão geral

O **LogiAssist** é um protótipo de assistente para apoiar a triagem inicial de ocorrências logísticas. A proposta é organizar as informações necessárias para analisar situações como atraso na entrega, rastreamento sem atualização, tentativa de entrega sem sucesso, divergência de status, avaria ou possível extravio, devolução e problemas com endereço.

O projeto foi desenvolvido como parte de um desafio prático de IA generativa, com foco em aplicação logística, uso de uma base de conhecimento estruturada e prevenção de respostas sem evidências.

## Problema que o projeto aborda

Ocorrências logísticas podem chegar com informações incompletas, descrições diferentes ou status divergentes entre sistemas. Isso dificulta a triagem e pode levar a conclusões precipitadas.

O LogiAssist propõe um fluxo inicial padronizado para:
- identificar a categoria da ocorrência;
- indicar quais informações precisam ser verificadas;
- apresentar ações recomendadas conforme os procedimentos cadastrados;
- explicitar o que não deve ser concluído sem evidências;
- encaminhar situações desconhecidas ou insuficientes para análise humana.

## Categorias contempladas

A base de conhecimento contém sete categorias:

1. Atraso na entrega
2. Rastreamento sem atualização
3. Tentativa de entrega sem sucesso
4. Divergência de status
5. Avaria ou possível extravio
6. Devolução
7. Problema com endereço

## Como funciona o protótipo

A implementação funcional foi experimentada no Google Colab com Python.

O fluxo demonstrado é:
1. Carregar a base de procedimentos em JSON.
2. Localizar a categoria correspondente na base.
3. Recuperar informações a verificar, ações recomendadas e restrições.
4. Identificar dados ausentes ou categorias não cadastradas.
5. Gerar uma resposta estruturada para apoiar a triagem.

A versão avaliada utiliza regras determinísticas em Python e a base JSON como fonte de referência. Um modelo local Qwen2.5-0.5B-Instruct também foi experimentado como camada de linguagem, mas apresentou inconsistências em alguns cenários. Por isso, não é utilizado como autoridade para definir status, confirmar extravio ou tomar decisões operacionais.

## Segurança e limites

O LogiAssist é um apoio à triagem, não substitui a análise humana nem os canais oficiais das transportadoras e plataformas.

O protótipo:
- não consulta rastreamento em tempo real;
- não confirma entrega, extravio, avaria ou responsabilidade sem evidências;
- não inventa prazos, causas, status ou procedimentos;
- não altera pedidos, endereços ou dados em sistemas externos;
- não abre chamados nem emite documentos;
- encaminha categorias desconhecidas e situações sem dados suficientes para análise humana.

Dados pessoais devem ser tratados apenas quando necessários e por canais autorizados.

## Avaliação realizada

Foram executados testes funcionais no protótipo:

| Verificação | Resultado |
|---|---|
| Categorias cadastradas | 7 |
| Categorias com estrutura válida | 7 |
| Cobertura estrutural da base | 100% |
| Identificação de informações incompletas | Aprovado |
| Reconhecimento de categoria desconhecida | Aprovado |
| Geração de respostas para as sete categorias | Verificada |

A cobertura de 100% refere-se à presença dos campos esperados nas sete categorias cadastradas. Não representa precisão, acurácia ou desempenho estatístico de um modelo de IA.

Os testes e suas limitações estão descritos em [docs/04-avaliacao-testes.md](./docs/04-avaliacao-testes.md).

## Estrutura do repositório

    .
    ├── data/
    │   └── procedimentos_logisticos.json
    ├── docs/
    │   ├── 01-documentacao-agente.md
    │   ├── 02-base-conhecimento.md
    │   ├── 03-prompts.md
    │   ├── 04-avaliacao-testes.md
    │   └── 05-pitch.md
    ├── src/
    │   └── README.md
    └── README.md

O notebook de experimentação foi salvo no Google Drive com o nome LogiAssist_Projeto_DIO.ipynb. A execução demonstrativa e os testes descritos neste repositório foram realizados no Google Colab.

## Próximas melhorias

- Ampliar os cenários de teste, incluindo entradas ambíguas e contraditórias.
- Construir um conjunto de casos de referência revisados por profissionais de logística.
- Medir separadamente a identificação de categoria, a detecção de dados ausentes e a conformidade das respostas.
- Evoluir a interface de demonstração.
- Avaliar integrações futuras com fontes oficiais, sempre com autorização e validação humana.

## Documentação

- [Documentação do agente](./docs/01-documentacao-agente.md)
- [Base de conhecimento](./docs/02-base-conhecimento.md)
- [Prompts e regras de comportamento](./docs/03-prompts.md)
- [Avaliação e testes](./docs/04-avaliacao-testes.md)
- [Roteiro do pitch](./docs/05-pitch.md)

---

**LogiAssist — organização, rastreabilidade e segurança na triagem de ocorrências logísticas.**
