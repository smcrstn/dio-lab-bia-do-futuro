# Base de Conhecimento — LogiAssist

## Objetivo

Reunir critérios de triagem e orientações iniciais para ocorrências de entrega. A base apoia a análise do profissional e reduz respostas genéricas.

## Dados utilizados

| Arquivo | Formato | Utilização |
|---|---|---|
| `procedimentos_logisticos.json` | JSON | Categorias, informações a verificar, ações sugeridas e limites de resposta |

O arquivo reúne sete categorias: atraso, rastreamento sem atualização, tentativa sem sucesso, divergência de status, avaria ou possível extravio, devolução e problema com endereço.

## Estrutura

Cada ocorrência apresenta:
- **Verificar:** informações necessárias para análise;
- **Ações:** verificações e próximos passos sugeridos;
- **Não concluir:** afirmações que não podem ser feitas sem evidência.

O arquivo também contém regras gerais e uma estrutura padrão de resposta.

## Adaptação dos dados

A base temática de logística substitui os exemplos financeiros do repositório original. Os cenários são genéricos e não contêm dados reais de clientes, pedidos ou transportadoras.

As orientações são referências para o protótipo, não políticas universais. Prazos e regras de reentrega, indenização ou devolução devem ser confirmados nos canais oficiais e procedimentos da empresa.

## Estratégia de integração

A aplicação Python carregará o arquivo JSON. A lógica do agente selecionará as informações relacionadas à ocorrência e as disponibilizará ao modelo junto com as instruções do prompt de sistema.

O agente deverá responder com base no conteúdo recuperado, pedir dados quando necessário e informar quando a base não oferecer orientação suficiente.

## Exemplo de contexto

**Categoria:** Rastreamento sem atualização

**Verificar:** data e hora do último evento, texto exato do status, prazo previsto e canal consultado.

**Ações:** confirmar o código, consultar o canal oficial, comparar o último evento com o prazo previsto e registrar a tratativa.

**Limite:** a ausência de atualização não comprova que a encomenda está perdida.

## Confiabilidade e limites

A base não fornece prazos fixos nem confirma eventos em tempo real. O agente deve separar relato, evidência e hipótese, solicitar informações complementares e recomendar validação humana quando necessário.
