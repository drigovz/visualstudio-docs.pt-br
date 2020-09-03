---
title: Pesquisando o conjunto de esquema | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656167"
---
# <a name="searching-the-schema-set"></a>Procurando pelo conjunto de esquema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Schema Explorer permite que você procurar o esquema define as seguintes maneiras:

- Pesquisa de palavras-chave.

- Pesquisa Esquema- específica.

## <a name="keyword-search"></a>Palavra-chave pesquisa
 Você executa pesquisas de palavra-chave inserindo uma subcadeia de caracteres na caixa de texto **Pesquisar schemaSet** da barra de ferramentas do Gerenciador de esquema XML.

 ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 XML Schema Explorer procura o esquema definido pelo seguinte:

- Alguns atributos de `name` ou de `ref` que corresponderem a palavra-chave especificada. Isso permite que você encontrar elementos, atributos, tipos, e assim por diante por nome.

- Atributos de `schemaLocation` de incluem instruções.

- Atributos de `namespace` de instruções de importação.

## <a name="schema-specific-search"></a>Pesquisar esquema específico
 XML Schema Explorer também inclui as pesquisas internos que você pode acessar usando o menu de contexto XML Schema Explorer. Para obter mais informações sobre menus de contexto disponíveis, consulte [menus de contexto](../xml-tools/context-menus-xml-schema-explorer.md). Você também pode executar uma pesquisa específica de esquema do modo de exibição iniciar; para obter mais informações, consulte a seção "detalhes do conjunto de esquema" no tópico [Start View](../xml-tools/start-view.md) .

## <a name="displaying-and-navigating-search-results"></a>Exibindo e navegando resultados de pesquisa
 Depois que a pesquisa é concluída, o painel de resultados de resumo é adicionado à barra de ferramentas com os resultados da pesquisa. Os resultados de pesquisa também são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical. Você pode navegar pelos resultados da pesquisa usando o botão **ir para o próximo resultado da pesquisa** e ir para os botões de **resultado da pesquisa anterior** no painel resultados do resumo da barra de ferramentas do Gerenciador de esquema XML; usando as teclas de teclado F3 e Shift + F3; ou clicando nas marcas de escala na barra de rolagem.

 Você pode adicionar os resultados da pesquisa ao espaço de trabalho clicando no botão **adicionar nós realçados ao espaço de trabalho** no painel resultados do resumo.

 ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Resultados da pesquisa de esclarecimento
 Para limpar os resultados da pesquisa, clique no botão **x** no painel resultados do resumo da barra de ferramentas de pesquisa do Gerenciador de esquema XML.

## <a name="see-also"></a>Consulte Também
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
