# Pitch — LogiAssist (3 minutos)

## Roteiro de apresentação

### 1. O problema (30 segundos)

Na rotina logística, as equipes recebem ocorrências como atraso na entrega, rastreamento sem atualização, tentativa de entrega sem sucesso, divergência de status, avaria ou possível extravio, devolução e problemas com endereço.

Muitas vezes, as informações chegam incompletas e estão distribuídas em diferentes consultas. Isso pode dificultar a triagem e levar a conclusões precipitadas, como afirmar que um pedido foi extraviado sem confirmação.

### 2. A solução (1 minuto)

Para apoiar essa etapa, desenvolvi o **LogiAssist**, um protótipo de assistente para triagem inicial de ocorrências logísticas.

A solução utiliza uma base de conhecimento estruturada em JSON, com sete categorias. Para cada ocorrência, estão definidos os pontos que precisam ser verificados, as ações recomendadas e aquilo que não deve ser concluído sem evidências.

Em Python, o protótipo consulta essas orientações e organiza uma resposta com a situação, as informações a verificar, as ações recomendadas e as restrições. Quando faltam dados ou a categoria não é reconhecida, o caso deve ser encaminhado para análise humana.

### 3. Demonstração (1 minuto)

Na demonstração, vou apresentar a base com as sete categorias e executar três situações.

Primeiro, uma ocorrência de atraso na entrega, para mostrar como o sistema organiza as verificações e as ações.

Depois, um caso de rastreamento sem atualização com informações incompletas. O teste identifica os campos que ainda precisam ser informados, em vez de inventar uma explicação.

Por último, vou testar uma categoria que não está cadastrada, como problema com pagamento. Nesse caso, o protótipo informa que não identificou a categoria e recomenda encaminhamento para análise humana.

Os testes estruturais confirmaram que as sete categorias possuem os campos previstos na base. Isso representa 100% de cobertura estrutural das categorias cadastradas, e não uma medida de precisão de inteligência artificial.

### 4. Diferencial e impacto (30 segundos)

O principal diferencial do LogiAssist é priorizar uma triagem organizada e segura. Ele não consulta transportadoras em tempo real, não altera pedidos e não confirma extravio, causas ou novas datas de entrega sem evidências.

Durante os experimentos, também avaliei o uso de um modelo de linguagem, mas os resultados apresentaram respostas inconsistentes. Por isso, o modelo não foi utilizado como autoridade para decisões. O protótipo atual se apoia nas regras e informações estruturadas, mantendo a validação humana.

Como próximos passos, a solução pode evoluir com validação de profissionais da área, mais cenários de teste, dados reais anonimizados, uma interface e integrações autorizadas.

**O LogiAssist não substitui o profissional de logística. Ele organiza informações para apoiar uma decisão humana mais consistente.**

---

## Apoio para a demonstração

1. Mostrar o arquivo `data/procedimentos_logisticos.json` e as sete categorias.
2. Executar uma ocorrência conhecida e apresentar as verificações, ações e restrições.
3. Executar o teste de informações incompletas e mostrar os campos identificados.
4. Executar o teste de categoria desconhecida e mostrar o encaminhamento para análise humana.
5. Apresentar o resumo da avaliação, explicando que os 100% representam cobertura estrutural.

## Checklist do pitch

- [ ] Duração máxima de 3 minutos.
- [ ] Problema claramente definido.
- [ ] Solução explicada sem prometer funções que o protótipo não possui.
- [ ] Demonstração prática dos testes.
- [ ] Diferencial e limitações apresentados com transparência.
- [ ] Áudio e vídeo com boa qualidade.
- [ ] Link do vídeo inserido abaixo.

## Link do vídeo

[Inserir aqui o link do pitch gravado]
