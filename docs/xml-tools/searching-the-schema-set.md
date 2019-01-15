---
title: XML Schema Explorer – pesquise o conjunto de esquema
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdb4a680fc2bbfc9a55d93d17f9ef95d45fc6186
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270067"
---
# <a name="search-the-schema-set"></a>O conjunto de esquema de pesquisa

O **XML Schema Explorer** permite pesquisar o esquema definido das seguintes maneiras:

-   Pesquisa de palavras-chave.

-   Pesquisa Esquema- específica.

## <a name="keyword-search"></a>Pesquisa de palavra-chave

 Executar pesquisas de palavra-chave inserindo uma subcadeia de caracteres a **pesquisa SchemaSet** caixa de texto da **XML Schema Explorer** barra de ferramentas.

 ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

 O **XML Schema Explorer** procura o esquema definido para os seguintes atributos:

-   Alguns atributos de `name` ou de `ref` que corresponderem a palavra-chave especificada. Você pode encontrar elementos, atributos, tipos e assim por diante, por nome.

-   Atributos de `schemaLocation` de incluem instruções.

-   Atributos de `namespace` de instruções de importação.

## <a name="schema-specific-search"></a>Pesquisar esquema específico

 O **XML Schema Explorer** também inclui as pesquisas internos que você pode acessar por meio do menu de contexto (atalho) da **XML Schema Explorer**. Para obter mais informações sobre menus de contexto disponíveis, consulte [menus de contexto](../xml-tools/context-menus-xml-schema-explorer.md). Você também pode executar uma pesquisa específica do esquema da exibição inicial; Para obter mais informações, consulte a seção de "detalhes para esquema" na [exibição inicial](../xml-tools/start-view.md) tópico.

## <a name="display-and-navigate-search-results"></a>Exibir e navegar pelos resultados da pesquisa

 Depois que a pesquisa é concluída, o painel de resultados de resumo é adicionado à barra de ferramentas com os resultados da pesquisa. Os resultados da pesquisa também são realçados na **XML Schema Explorer** e marcados por escalas na barra de rolagem vertical. Você pode navegar os resultados da pesquisa usando o **ir para próximo resultado da pesquisa** e **vá ao resultado da pesquisa anterior** botões no painel de resultados de resumo do **XML Schema Explorer**barra de ferramentas; usando as teclas do teclado **F3** e **Shift**+**F3**; ou clicando-se as marcas de escala na barra de rolagem.

 Você pode adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.

 ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Limpar resultados da pesquisa

 Para limpar os resultados da pesquisa, clique o **x** botão no painel de resultados de resumo de **XML Schema Explorer** barra de ferramentas de pesquisa.

## <a name="see-also"></a>Consulte também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)