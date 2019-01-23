---
title: Usar o sumário do Help Viewer
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 667295e0343b7523f039770b02a7544c36906db2
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "54406074"
---
# Como: Localizar tópicos no sumário

Na guia **Sumário**, você pode usar o sumário para localizar informações. O sumário é uma lista expansível que contém todos os tópicos nos livros instalados. Para obter informações de acessibilidade sobre como navegar pelo sumário, consulte [Teclas de atalho (Visualizador da Ajuda)](../help-viewer/shortcut-keys.md).

> [!IMPORTANT]
> O escopo dos tópicos disponíveis no sumário depende do filtro selecionado.

## Filtrar o sumário

Você pode filtrar o sumário para restringir o escopo dos tópicos que aparecem na guia **Sumário**. Títulos aparecem na lista somente se contiverem a raiz do termo que você especificar. Por exemplo, se você especificar "solucionar" como filtro, somente títulos que contiverem "solucionar" ou "solucionar problemas" aparecerão. Nós cujos títulos não contiverem o termo serão recolhidos para um único nó com um sinal de reticências (**...**).

1.  Escolha a guia **Sumário**.

2.  Na caixa de texto **Filtrar Conteúdo**, digite um termo.

> [!NOTE]
> Se o filtro demorar muito para ser executado, você pode exibir resultados mais rapidamente usando o operador de pesquisa avançada `title:`.

## Sincronizar um tópico com o sumário

Se tiver aberto um tópico usando os recursos de pesquisa de texto completo ou o índice, você pode determinar onde este tópico está no sumário sincronizando o sumário com a janela do tópico.

1.  Exibir um tópico.

2.  Clique no botão **Mostrar Tópico no Conteúdo** na barra de ferramentas ou pressione **Ctrl**+**S**.

     A guia **Sumário** é aberta e exibe o local do tópico no Sumário.

## Consulte também

- [Como: Localizar tópicos no índice](../help-viewer/find-topics-index.md)
- [Como: Pesquisar tópicos](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)