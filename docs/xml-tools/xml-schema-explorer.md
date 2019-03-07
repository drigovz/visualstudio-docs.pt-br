---
title: XML Schema Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24dd2c13a0d2d4d2a98d11e5154b96261d19d492
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525704"
---
# <a name="xml-schema-explorer"></a>XML Schema Explorer

O **XML Schema Explorer** é integrado ao Microsoft Visual Studio e o editor de XML para que você possa trabalhar com esquemas XSD (linguagem) de definição de esquema XML. Quando você abre um arquivo de esquema XML, o **do conjunto de esquema** nó aparece na **XML Schema Explorer**. Todos os esquemas incluídos, importados ou redefinidos para seu arquivo de destino, bem como todos os arquivos que são referenciados por meio de um `include` ou `import` instrução, também aparecem na **XML Schema Explorer**.

 O **XML Schema Explorer** permite que você faça o seguinte:

-   Obter uma visão geral rápido do conjunto de esquema.

-   Procurar e navegar na árvore.

-   Realizar pesquisas de palavra-chave e específicas do esquema. Para obter mais informações, consulte [procurando o conjunto de esquema](../xml-tools/searching-the-schema-set.md).

-   Adicionar os resultados da pesquisa à exibição de gráfico ou modo de exibição do modelo de conteúdo

-   Classificar a árvore pela ordem de documento, tipo ou nome. Para obter mais informações, consulte [classificação, filtragem e agrupamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

-   Abra o editor de XML e saltar para locais de código no arquivo XSD. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

-   Gere o exemplo de XML para elementos globais.

O **XML Schema Explorer** fornece uma exibição hierárquica do esquema definido por meio de uma exibição de árvore. O **XML Schema Explorer** também fornece pesquisa, filtragem, navegação e classificação. Para acessar o **XML Schema Explorer**, faça o seguinte:

-   Se você estiver usando o [iniciar o modo de exibição](../xml-tools/start-view.md), clique no **XML Schema Explorer** link.

-   Se você estiver usando o [exibição de gráfico](../xml-tools/graph-view.md) ou o [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) e tiver nós em seu espaço de trabalho, use o menu de contexto (clique com botão direito) para selecionar o **XML Schema Explorer**.

-   Você também pode selecionar o **XML Schema Explorer** da **exibição** menu.

-   Você pode acessar o **XML Schema Explorer** de uma *. vb* arquivo que tem um literal XML do Visual Basic associado com um *. xsd* arquivo. Para ver o esquema definido **XML Schema Explorer**, um nó XML em um literal XML ou uma importação de namespace XML com o botão direito e selecione o **Mostrar no Schema Explorer** comando. Para obter mais informações, consulte [literais de integração do XML com XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Exibição de árvore
 O **XML Schema Explorer** informações de conjunto de esquemas de exibições pré-compiladas em uma estrutura de árvore. A estrutura de árvore é organizada da seguinte maneira:

-   No nível superior está o nó do conjunto de esquema.

-   O segundo nível contém os namespaces.

-   O terceiro nível contém os arquivos.

-   O quarto nível contém os nós globais. Isso pode incluir elementos, grupos, tipos complexos, tipos simples, atributos, grupos de atributo e instruções `include`, `import` e `redefine`.

A seguir veja um exemplo de uma estrutura de árvore:

![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Seleção e ativação
 Para realçar e selecionar um nó, clique uma vez no Schema Explorer.

 Para ativar um nó, clique duas vezes nele ou pressione **Enter** quando o nó é selecionado.

-   Ativar um nó abre o arquivo no qual o nó está definido (se o arquivo já não estiver aberto) e seleciona o nó no arquivo.

-   Ativar um nó de arquivo abre o arquivo selecionado (se ele já não estiver aberto) e destaca o nó `<schema>`.

-   Ativar um SchemaSet ou um nó de namespace não fará nada.

## <a name="drag-and-drop-nodes"></a>Arraste e solte os nós
 Você pode arrastar e soltar nós globais, nós de arquivo e nós de namespace em uma exibição do Designer XSD. Se a exibição atual for o [iniciar o modo de exibição](../xml-tools/start-view.md), arrastar um nó para o modo de exibição será aberto o [modo de exibição gráfico](../xml-tools/graph-view.md). Se a exibição atual for o [modo de exibição do modelo de conteúdo](../xml-tools/content-model-view.md) ou modo de exibição de gráfico, o modo de exibição não será alterado quando você remove um nó nela.

 Soltar arquivos na exibição adicionará todos os nós globais no arquivo para o [espaço de trabalho do Designer XSD](../xml-tools/xml-schema-designer-workspace.md). Soltar namespaces na exibição adicionará todos os nós globais no namespace para o workspace. O workspace é compartilhado entre todas as visualizações.

 Você não pode arrastar e soltar nós locais ou importações.

## <a name="see-also"></a>Consulte também

- [Como: Adicionar nós ao espaço de trabalho do XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)