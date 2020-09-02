---
title: XML Schema Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04c6415fed131abc5a102f6ec15c69e33f21fd68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592341"
---
# <a name="xml-schema-explorer"></a>XML Schema Explorer

O **XML Schema Explorer** é integrado com Microsoft Visual Studio e o editor de XML para permitir que você trabalhe com esquemas XSD (linguagem de definição de esquema XML). Quando você abre um arquivo de esquema XML, o nó de **conjunto de esquema** aparece no **XML Schema Explorer**. Todos os esquemas incluídos, importados ou redefinidos para seu arquivo de destino, bem como todos os arquivos que são referenciados por meio de uma `include` `import` instrução ou, também aparecem no **XML Schema Explorer**.

O **XML Schema Explorer** permite que você faça o seguinte:

- Obter uma visão geral rápido do conjunto de esquema.

- Procurar e navegar na árvore.

- Realizar pesquisas de palavra-chave e específicas do esquema. Para obter mais informações, consulte [pesquisando o conjunto de esquema](../xml-tools/searching-the-schema-set.md).

- Adicionar os resultados da pesquisa ao modo de exibição de gráfico ou de modelo de conteúdo

- Classificar a árvore pela ordem de documento, tipo ou nome. Para obter mais informações, consulte [classificar, filtrar e agrupar](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Abra o editor de XML e salte para os locais de código no arquivo XSD. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

- Gere o exemplo de XML para elementos globais.

O **XML Schema Explorer** fornece uma exibição hierárquica do conjunto de esquema por meio de uma exibição de árvore. O **XML Schema Explorer** também fornece pesquisa, filtragem, navegação e classificação. Para acessar o **XML Schema Explorer**, siga um destes procedimentos:

- Se você estiver na [exibição iniciar](../xml-tools/start-view.md), clique no link do **Gerenciador de esquema XML** .

- Se você estiver na [exibição de gráfico](../xml-tools/graph-view.md) ou no [modo de exibição de modelo de conteúdo](../xml-tools/content-model-view.md) e tiver nós em seu espaço de trabalho, use o menu de contexto (clique com o botão direito do mouse) para selecionar o Gerenciador de **esquema XML**.

- Você também pode selecionar o **Gerenciador de esquema XML** no menu **Exibir** .

- Você pode acessar o **XML Schema Explorer** de um arquivo *. vb* que tem um literal XML Visual Basic associado a um arquivo *. xsd* . Para ver o conjunto de esquema no **Gerenciador de esquema XML**, clique com o botão direito do mouse em um nó XML em um literal XML ou em uma importação de namespace XML e selecione o comando **Mostrar no Gerenciador de esquema** . Para obter mais informações, consulte [integração de literais XML com o XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Modo de exibição de árvore
O **XML Schema Explorer** exibe informações de conjunto de esquema pré-compilado em uma estrutura de árvore. A estrutura de árvore é organizada da seguinte maneira:

- No nível superior está o nó do conjunto de esquema.

- O segundo nível contém os namespaces.

- O terceiro nível contém os arquivos.

- O quarto nível contém os nós globais. Isso pode incluir elementos, grupos, tipos complexos, tipos simples, atributos, grupos de atributo e instruções `include`, `import` e `redefine`.

A seguir veja um exemplo de uma estrutura de árvore:

![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Seleção e ativação
Para realçar e selecionar um nó, clique uma vez no Schema Explorer.

Para ativar um nó, clique duas vezes nele ou pressione **Enter** quando o nó for selecionado.

- Ativar um nó abre o arquivo no qual o nó está definido (se o arquivo já não estiver aberto) e seleciona o nó no arquivo.

- Ativar um nó de arquivo abre o arquivo selecionado (se ele já não estiver aberto) e destaca o nó `<schema>`.

- Ativar um SchemaSet ou um nó de namespace não fará nada.

## <a name="drag-and-drop-nodes"></a>Arrastar e soltar nós
Você pode arrastar e soltar nós globais, nós de arquivo e nós de namespace em uma exibição do Designer XSD. Se o modo de exibição atual for o [modo de exibição de início](../xml-tools/start-view.md), arrastar um nó para a exibição abrirá o modo de exibição de [gráfico](../xml-tools/graph-view.md). Se a exibição atual for o modo de [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) ou de gráfico, a exibição não será alterada quando você soltar um nó nele.

O descarte de arquivos na exibição adicionará todos os nós globais no arquivo ao [espaço de trabalho do designer XSD](../xml-tools/xml-schema-designer-workspace.md). Soltar namespaces na exibição adicionará todos os nós globais no namespace para o workspace. O workspace é compartilhado entre todas as visualizações.

 Você não pode arrastar e soltar nós locais ou importações.

## <a name="see-also"></a>Confira também

- [Como adicionar nós ao espaço de trabalho do XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
