---
title: XML Schema Explorer-Pesquisar o conjunto de esquema
description: Saiba como fazer uma pesquisa de palavra-chave e uma pesquisa específica de esquema do conjunto de esquema no XML Schema Explorer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f924e46fa4d32fbea9071bd8a19268f2ee1652e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891872"
---
# <a name="search-the-schema-set"></a>Pesquisar o conjunto de esquemas

O **XML Schema Explorer** permite que você pesquise o conjunto de esquema das seguintes maneiras:

- Pesquisa de palavras-chave.

- Pesquisa Esquema- específica.

## <a name="keyword-search"></a>Pesquisa de palavra-chave

Você executa pesquisas de palavra-chave inserindo uma subcadeia de caracteres na caixa de texto **Pesquisar schemaSet** da barra de ferramentas do **Gerenciador de esquema XML** .

![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

O **XML Schema Explorer** pesquisa o conjunto de esquema para os seguintes atributos:

- Alguns atributos de `name` ou de `ref` que corresponderem a palavra-chave especificada. Você pode encontrar elementos, atributos, tipos e assim por diante, por nome.

- Atributos de `schemaLocation` de incluem instruções.

- Atributos de `namespace` de instruções de importação.

## <a name="schema-specific-search"></a>Pesquisa específica do esquema

O **XML Schema Explorer** também inclui pesquisas internas que você pode acessar usando o menu de contexto (clique com o botão direito do mouse) do **XML Schema Explorer**. Para obter mais informações sobre menus de contexto disponíveis, consulte [menus de contexto](../xml-tools/context-menus-xml-schema-explorer.md). Você também pode executar uma pesquisa específica de esquema do modo de exibição iniciar; para obter mais informações, consulte a seção "detalhes do conjunto de esquema" no tópico [Start View](../xml-tools/start-view.md) .

## <a name="display-and-navigate-search-results"></a>Exibir e navegar pelos resultados da pesquisa

Depois que a pesquisa é concluída, o painel de resultados de resumo é adicionado à barra de ferramentas com os resultados da pesquisa. Os resultados da pesquisa também são realçados no **XML Schema Explorer** e marcados por tiques na barra de rolagem vertical. Você pode navegar pelos resultados da pesquisa usando o botão **ir para o próximo resultado da pesquisa** e ir para os botões de **resultado da pesquisa anterior** no painel resultados do resumo da barra de ferramentas do **Gerenciador de esquema XML** ; usando as teclas de teclado **F3** e **Shift** + **F3**; ou clicando nas marcas de escala na barra de rolagem.

Você pode adicionar os resultados da pesquisa ao espaço de trabalho clicando no botão **adicionar nós realçados ao espaço de trabalho** no painel resultados do resumo.

![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Limpar resultados da pesquisa

Para limpar os resultados da pesquisa, clique no botão **x** no painel resultados do resumo da barra de ferramentas de pesquisa do **Gerenciador de esquema XML** .

## <a name="see-also"></a>Confira também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
