# Selo Pasto Baixo Carbono

**Acesso:** [aluisiopereirae.github.io/selo](https://aluisiopereirae.github.io/selo/)

Plataforma web para calcular a emissão de metano de fazendas de gado de corte a pasto, classificar a fazenda em um nível de selo (Bronze, Prata ou Ouro), indicar o que falta para chegar ao Ouro e emitir etiquetas com QR Code para as embalagens de carne.

Tudo roda em um único arquivo HTML, direto no navegador. Não precisa de instalação, servidor nem banco de dados.

> O selo e os seus limites são uma proposta de critério para pesquisa e demonstração. Eles não constituem certificação oficial da Embrapa.

## Como usar

1. Baixe o arquivo `Selo_Pasto_Baixo_Carbono.html`.
2. Abra no navegador (Chrome, Edge ou Firefox).
3. Preencha os dados da fazenda. Os resultados são atualizados na hora.

Os dados ficam salvos no próprio navegador. O botão **Restaurar exemplo** volta aos valores de exemplo.

Para publicar no GitHub Pages, renomeie o arquivo para `index.html`, envie para o repositório e ative o Pages em **Settings → Pages**.

## Como a plataforma funciona

A página é dividida em etapas numeradas.

| Etapa | O que faz |
|---|---|
| **1 · Fazenda** | Nome, área e duração da estação seca e da chuvosa. |
| **2 · Forragem** | Composição do pasto em cada estação. Você pode escolher um dos sistemas da planilha ou informar valores próprios. |
| **3 · Rebanho** | Número de animais, peso, ganho de peso diário e suplementação de cada categoria (bezerros, recria, adultos etc.). |
| **4 · Emissões** | Metano emitido por categoria e por estação, em kg por ano e por kg de ganho de peso. |
| **5 · Comparação** | Compara a fazenda com os sistemas de referência da planilha. |
| **6 · Critérios** | Linha de base e redução mínima exigida para cada nível do selo. A entidade certificadora pode ajustar esses valores. |
| **7 · Plano Ouro** | Mostra o que precisa mudar no manejo para chegar ao Selo Ouro, como aumentar o ganho de peso, ajustar o lote ou suplementar. |
| **8 · Emitir** | Emite o selo com um código único e gera a etiqueta e o resumo para impressão. |
| **9 · Validar** | Confere se um selo é verdadeiro, se está dentro da validade e se não foi cancelado. |

No painel lateral ficam sempre visíveis o nível atual do selo, a intensidade de emissão, o total de metano e de CO₂e e as emissões evitadas em relação à linha de base.

## Como o selo é calculado

1. A plataforma estima o consumo de cada animal e o metano que ele produz, usando a composição do pasto, o peso, o ganho de peso e a suplementação.
2. Ela soma o metano do ano inteiro e divide pelo ganho de peso total do rebanho. O resultado é a **intensidade de emissão**: quanto metano a fazenda emite por kg de carne produzida.
3. Depois compara essa intensidade com a linha de base.

| Nível | Redução mínima em relação à linha de base (padrão) |
|---|---|
| Bronze | 10% |
| Prata | 25% |
| Ouro | 40% |

**Referências:** BR-Corte 5.0 (consumo de matéria seca) e Ribeiro et al. (2020) (metano entérico). O metano é convertido em CO₂e pelo GWP₁₀₀ do IPCC AR6 (27). A linha de base padrão é o sistema de pastejo alternado na seca, calculado com os dados da planilha.

## Emissão do selo e etiquetas

Somente a **entidade certificadora** emite selos válidos. Para isso, ela usa um arquivo de chave que só ela possui.

1. Na seção **8 · Emitir**, preencha a certificadora, o município, o lote e a validade.
2. Carregue o arquivo de chave da certificadora.
3. Clique em **Emitir selo assinado**. O selo recebe um identificador único, por exemplo `SPBC-2026-9P8R-BHPV`.
4. Baixe ou imprima o material:
   - **Etiqueta** em PNG ou SVG;
   - **Folha A4** com 1, 4 ou 8 etiquetas para colar nas embalagens;
   - **Resumo da emissão** em A4, que pode ser impresso ou salvo em PDF;
   - **Dados de verificação**, um arquivo para auditoria.

Sem o arquivo de chave, a plataforma gera apenas um **rascunho**. Ele serve para conferir o layout e é recusado na validação.

Cada emissão fica registrada no navegador. O registro pode ser exportado em CSV, e cada selo pode ser marcado como revogado.

## Validação

Qualquer pessoa pode conferir um selo:

- lendo o **QR Code** da etiqueta com o celular, ou
- colando o código do selo na seção **9 · Validar**.

A plataforma informa uma destas situações:

| Resultado | Significado |
|---|---|
| ✅ **Válido** | O selo foi emitido pela certificadora e não foi alterado. |
| ⚠️ **Vencido** | O selo é verdadeiro, mas passou da data de validade. |
| ❌ **Não válido** | O código foi alterado ou não foi emitido pela certificadora. |
| ❌ **Revogado** | A certificadora cancelou o selo. |

Com o arquivo de dados de verificação, o auditor também recalcula as emissões e confere se os números batem com o selo.

## Antes de colocar em uso real

- [ ] Gere a chave da certificadora em **8 · Emitir → Criar a chave da certificadora** e guarde o arquivo baixado em local seguro.
- [ ] Cole o trecho gerado na lista `CHAVES_CERTIFICADORAS`, no código da página.
- [ ] Remova a chave de demonstração (`DEMO-2026`) dessa lista.
- [ ] Publique a página em um endereço público e informe esse endereço no campo do QR Code.
- [ ] Para cancelar um selo, inclua o identificador na lista `REVOGADOS` e publique a página de novo.

O arquivo `chave-privada-DEMONSTRACAO.json` serve apenas para testes. Não use essa chave para emitir selos reais.

## Arquivos

```
Selo_Pasto_Baixo_Carbono.html     plataforma completa (arquivo único)
chave-privada-DEMONSTRACAO.json   chave de teste, apenas para demonstração
README.md                         este arquivo
```

## Créditos

- Equações e dados: planilha *Prediction Methane par catégorie* (sugestão do Prof. André, UFMT Sinop, 2024).
- Visual: Design System da Embrapa.
- Geração de QR Code: [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) (Kazuhiko Arase, licença MIT).

Embrapa Maranhão · Praça da República, 147 – Diamante, São Luís – MA · CEP 65020-500 · (98) 3878-2234
