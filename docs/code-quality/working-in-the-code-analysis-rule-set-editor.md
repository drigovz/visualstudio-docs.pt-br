---
title: Trabalhar no editor de conjunto de regras de análise de Código
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffaf964b24fea41d8e364d610806ba92980b1dc7
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659173"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Usar o editor de conjunto de regras de análise de código

O editor de conjunto de regras de análise de código permite especificar as regras incluídas em um conjunto de regras personalizadas e definir a gravidade das violações de regra.

A tabela a seguir mostra as opções de gravidade:

|Ação (severidade)|Descrição|
|-|-|
|Aviso|Gera um aviso no **lista de erros** e também no momento da compilação.|
|Erro|Gera um erro na **lista de erros** e também no momento da compilação.|
|Informações|Gera uma mensagem no **lista de erros**.|
|Hidden|A violação não é visível para o usuário. No entanto, o IDE é notificado sobre a violação.|
|Nenhum|A regra foi suprimida. O comportamento é o mesmo que se a regra foi removida do conjunto de regras.|

O editor exibe as regras em uma estrutura de árvore que agrupa as regras por um campo de conjunto de regras que você especificar. Para adicionar ou remover regras de um conjunto de regras, execute uma ou mais das seguintes etapas:

- Marque ou desmarque a caixa de seleção do nó de grupo para adicionar ou remover todas as regras no grupo. Quando você seleciona um grupo, todas as regras são definidas para a ação de **aviso** .

   > [!TIP]
   > Você pode alterar o modo como as regras são agrupadas na lista suspensa **Agrupar por** .

- Clique no campo **ação** de um grupo, especifique a ação a ser aplicada a todas as regras no grupo.

- Marque ou desmarque a caixa de seleção de uma regra individual. Quando você marca a caixa de seleção para uma regra, a regra é definida como a ação de **aviso** .

## <a name="toolbar"></a>Barra de ferramentas

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

Os campos de conjunto de regras exibem informações sobre um conjunto de regras e podem ser usados para classificar e agrupar a lista de regras. Para exibir ou ocultar campos, selecione **Opções de coluna** na barra de ferramentas do editor de conjunto de regras e marque ou desmarque as caixas de seleção dos campos a serem mostrados ou ocultados.

A tabela a seguir descreve os campos de um conjunto de regras:

|Campo|Descrição|
|-----------|-----------------|
|**ID**|O identificador da regra.|
|**Categoria**|Além de sua associação em conjuntos de regras, as regras de análise de código também são agrupadas por categoria. Para obter mais informações, consulte [avisos de análise de código](/dotnet/fundamentals/code-analysis/quality-rules/index).|
|**Nome**|O título da regra.|
|**Namespace**|O namespace da regra.|
|**Tipo de destino**|Indica se a regra é para código nativo, gerenciado ou de banco de dados.|
|**Ação**|A ação realizada quando a regra é violada em uma execução de análise de código. Você pode editar o campo de **ação** .|
|**Conjuntos de regras de origem**|O conjunto de regras que contém a regra.|

## <a name="sort-and-filter-rule-sets"></a>Classificar e filtrar conjuntos de regras

Nos cabeçalhos de coluna da grade de conjunto de regras, você pode classificar e filtrar as regras pelos valores do campo.

- Para classificar as listas de conjuntos de regras, selecione o cabeçalho de coluna do campo pelo qual você deseja classificar. Se os conjuntos de regras forem agrupados, cada grupo será classificado individualmente.

- Para filtrar os conjuntos de regras pelo valor de um campo, selecione o botão de filtro no cabeçalho da coluna do campo pelo qual você deseja filtrar. Marque as caixas de seleção dos valores que você deseja mostrar e desmarque as caixas de seleção dos valores que você deseja ocultar.

## <a name="see-also"></a>Consulte também

- [Criar um conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md)
