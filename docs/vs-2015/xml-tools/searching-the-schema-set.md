---
title: Pesquisando o conjunto de esquema | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d388db50ae935ef85b720177bd31c832a353d31
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145174"
---
# <a name="searching-the-schema-set"></a>Procurando pelo conjunto de esquema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Schema Explorer permite que você procurar o esquema define as seguintes maneiras:  
  
- Pesquisa de palavras-chave.  
  
- Pesquisa Esquema- específica.  
  
## <a name="keyword-search"></a>Palavra-chave pesquisa  
 Executar pesquisas de palavra-chave inserindo uma subcadeia de caracteres a **pesquisa SchemaSet** caixa de texto da barra de ferramentas XML Schema Explorer.  
  
 ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML Schema Explorer procura o esquema definido pelo seguinte:  
  
- Alguns atributos de `name` ou de `ref` que corresponderem a palavra-chave especificada. Isso permite que você encontrar elementos, atributos, tipos, e assim por diante por nome.  
  
- Atributos de `schemaLocation` de incluem instruções.  
  
- Atributos de `namespace` de instruções de importação.  
  
## <a name="schema-specific-search"></a>Pesquisar esquema específico  
 XML Schema Explorer também inclui as pesquisas internos que você pode acessar usando o menu de contexto XML Schema Explorer. Para obter mais informações sobre menus de contexto disponíveis, consulte [Menus de contexto](../xml-tools/context-menus-xml-schema-explorer.md). Você também pode executar uma pesquisa específica do esquema da exibição inicial; Para obter mais informações, consulte a seção de "detalhes para esquema" na [exibição inicial](../xml-tools/start-view.md) tópico.  
  
## <a name="displaying-and-navigating-search-results"></a>Exibindo e navegando resultados de pesquisa  
 Depois que a pesquisa é concluída, o painel de resultados de resumo é adicionado à barra de ferramentas com os resultados da pesquisa. Os resultados de pesquisa também são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical. Você pode navegar os resultados da pesquisa usando o **ir para próximo resultado da pesquisa** e **vá ao resultado da pesquisa anterior** botões no painel de resultados de resumo da barra de ferramentas XML Schema Explorer; usando as teclas do teclado F3 e SHIFT+F3; ou clicando-se as marcas de escala na barra de rolagem.  
  
 Você pode adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.  
  
 ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Resultados da pesquisa de esclarecimento  
 Para limpar os resultados da pesquisa, clique o **x** botão no painel de resultados de resumo da barra de ferramentas XML Schema de pesquisa.  
  
## <a name="see-also"></a>Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
