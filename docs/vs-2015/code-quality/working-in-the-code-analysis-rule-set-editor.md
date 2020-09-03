---
title: Trabalhando no editor de conjunto de regras de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621503"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Trabalhando no Editor de Conjunto de Regras de Análise do Código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor de conjunto de regras de análise de código permite que você especifique as regras que são incluídas em um conjunto de regras personalizadas e para especificar a ação. Você também pode especificar a ação a ser tomada quando a análise de código encontrar uma violação da regra.

|Ação|Descrição|
|------------|-----------------|
|**Aviso**|Gera um aviso na janela de **lista de erros** .|
|**Erro**|Gera um erro na janela de **lista de erros** .|
|**Nenhuma**|Desabilita a regra.|

 O editor exibe as regras em uma estrutura de árvore que agrupa as regras por um campo de conjunto de regras que você especificar. Para adicionar ou remover regras de um conjunto de regras, execute uma ou mais das seguintes etapas:

- Marque ou desmarque a caixa de seleção do nó de grupo para adicionar ou remover todas as regras no grupo. Quando você seleciona um grupo, todas as regras são definidas para a ação de **aviso** .

- Clique no campo **ação** de um grupo e especifique a ação a ser aplicada a todas as regras no grupo.

- Marque ou desmarque a caixa de seleção de uma regra individual. Quando você marca a caixa de seleção para uma regra, a regra é definida como a ação de aviso.

## <a name="rule-set-editor-toolbar"></a>Barra de ferramentas do editor de conjunto de regras
 Você pode usar a barra de ferramentas do editor de conjunto de regras para agrupar, filtrar e Pesquisar os dados que aparecem na grade conjunto de regras.

 A tabela a seguir descreve os controles na barra de ferramentas do editor de conjunto de regras.

|Controle ToolBar|Descrição|
|---------------------|-----------------|
|**Expandir Tudo**|Mostra as regras em todos os grupos.|
|**Recolher Tudo**|Oculta as regras em todos os grupos.|
|**Agrupar por**|Especifica o campo pelo qual as regras são agrupadas. Clique **\<None>** para mostrar as regras sem grupos.|
|**Opções de Coluna**|Especifica os campos de regra a serem exibidos.|
|**Ocultar regras que não se aplicam à solução atual**|Mostra ou oculta regras que não são do mesmo tipo de destino que a solução.|
|**Mostrar regras que podem gerar erros de análise de código**|Mostra ou oculta as regras que são atribuídas à ação de erro.|
|**Mostrar regras que podem gerar avisos de análise de código**|Mostra ou oculta as regras que são atribuídas à ação de aviso.|
|**Mostrar regras que não estão habilitadas**|Mostra ou oculta as regras que são atribuídas à ação None.|
|**Adicionar ou remover conjuntos de regras filho**|Adiciona ou remove as regras nos conjuntos de regras selecionados.|
|**Regras de pesquisa**|Pesquisa todos os valores de campo para a cadeia de caracteres que você especificar.|

## <a name="rule-set-fields"></a>Campos de conjunto de regras
 Os campos de conjunto de regras exibem informações sobre um conjunto de regras e podem ser usados para classificar e agrupar a lista de regras. Para exibir ou ocultar campos, clique em **Opções de coluna** na barra de ferramentas do editor de conjunto de regras e marque ou desmarque as caixas de seleção dos campos a serem mostrados ou ocultados.

 A tabela a seguir descreve os campos de um conjunto de regras.

|Campo|Descrição|
|-----------|-----------------|
|**ID**|O identificador da regra.|
|**Categoria**|Além de sua associação em conjuntos de regras, as regras de análise de código também são agrupadas por categoria. Para obter mais informações, consulte [análise de código para avisos de código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nome**|O título da regra.|
|**Namespace**|O namespace da regra.|
|**Tipo de destino**|Indica se a regra é para código nativo, gerenciado ou de banco de dados.|
|**Ação**|A ação realizada quando a regra é violada em uma execução de análise de código.<br /><br /> **Aviso** -gera um aviso.<br /><br /> **Erro** -gera um erro.<br /><br /> **Nenhum** – desabilita a regra.<br /><br /> Você pode editar o campo de ação. Definir o valor como nenhum é o mesmo que desmarcar a caixa de seleção da regra.|
|**Conjuntos de regras de origem**|O conjunto de regras que contém a regra.|

## <a name="sorting-and-filtering-rule-sets"></a>Classificando e filtrando conjuntos de regras
 Nos cabeçalhos de coluna da grade de conjunto de regras, você pode classificar e filtrar as regras pelos valores do campo.

- Para classificar as listas de conjuntos de regras, clique no cabeçalho de coluna do campo pelo qual você deseja classificar. Se os conjuntos de regras forem agrupados, cada grupo será classificado individualmente.

- Para filtrar os conjuntos de regras pelo valor de um campo, clique no botão de filtro no cabeçalho da coluna do campo pelo qual você deseja filtrar. Marque as caixas de seleção dos valores que você deseja mostrar e desmarque as caixas de seleção dos valores que você deseja ocultar.
