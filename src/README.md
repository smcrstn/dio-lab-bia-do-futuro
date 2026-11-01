# Implementação do LogiAssist

Esta pasta reúne as orientações técnicas da implementação do protótipo LogiAssist.

## Ambiente utilizado

- **Google Colab:** ambiente de desenvolvimento e execução do notebook.
- **Python:** linguagem utilizada na lógica de triagem e geração das respostas.
- **JSON:** formato da base de conhecimento com as sete categorias logísticas.
- **Transformers:** biblioteca utilizada no experimento com o modelo local Qwen2.5-0.5B-Instruct.

## Fluxo implementado no notebook

O protótipo desenvolvido no Google Colab executa as seguintes etapas:

1. Carrega a base de conhecimento JSON hospedada no repositório.
2. Localiza uma ocorrência cadastrada pelo código ou categoria.
3. Recupera verificações, ações recomendadas e restrições.
4. Organiza uma resposta estruturada com Python.
5. Identifica campos obrigatórios ausentes em um cenário de teste.
6. Reconhece categorias não cadastradas e recomenda análise humana.

## Fonte da base de conhecimento

O arquivo utilizado pelo notebook é:

[data/procedimentos_logisticos.json](../data/procedimentos_logisticos.json)

A base contém sete categorias e orientações para apoiar a triagem. Ela não representa uma conexão em tempo real com transportadoras, marketplaces ou sistemas internos.

## Modelo de linguagem

Foi realizado um experimento com o modelo local Qwen/Qwen2.5-0.5B-Instruct, utilizando a biblioteca Transformers.

Durante os testes, o modelo apresentou inconsistências e conclusões sem evidências suficientes em alguns cenários. Por esse motivo, a versão funcional avaliada prioriza regras determinísticas em Python e utiliza o JSON como fonte de referência. O modelo não deve decidir sozinho sobre status, extravio, responsabilidade ou prazos.

## Como reproduzir a demonstração

O notebook de desenvolvimento está salvo no Google Drive com o nome LogiAssist_Projeto_DIO.ipynb.

Para reproduzir a demonstração:

1. Abra o Google Colab.
2. Abra o notebook salvo no Google Drive.
3. Execute as células em ordem, começando pela instalação/importação das dependências e pelo carregamento da base JSON.
4. Execute as células de validação e os testes das categorias.

A instalação do ambiente de experimentação com Transformers foi feita com:

    !pip install -q -U transformers accelerate

A execução do notebook pode exigir download inicial dos arquivos do modelo e das dependências. O desempenho depende dos recursos disponibilizados pelo ambiente do Colab.

## Limitações

- Não há aplicação web independente ou interface Streamlit/Gradio implementada nesta versão.
- Não há integração com APIs de rastreamento ou sistemas de transportadoras.
- O protótipo não altera pedidos, endereços, status ou registros externos.
- Os testes realizados são funcionais e controlados; não constituem validação estatística em produção.

Consulte [docs/04-avaliacao-testes.md](../docs/04-avaliacao-testes.md) para os cenários avaliados e os resultados registrados.
