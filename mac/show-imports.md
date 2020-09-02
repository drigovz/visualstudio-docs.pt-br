---
title: Mostrar itens de importação
description: Use mostrar itens de importação para expandir o IntelliSense no Visual Studio para Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451506"
---
# <a name="show-import-items"></a>Mostrar itens de importação

Visual Studio para Mac pode mostrar todos os tipos disponíveis, mesmo que eles não sejam importados para seu projeto, na sua lista de conclusão do IntelliSense. Ao selecionar um item que não é importado, a `using` instrução correta será adicionada ao arquivo de origem.

![Mostrar visão geral de itens de importação](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Como habilitar

Para habilitar esse recurso, abra **preferências** por meio de preferências do **Visual Studio**  >  **Preferences** e navegue até o **Editor de texto**  >  **IntelliSense**. Marque a caixa **Mostrar itens de importação** para habilitar itens adicionais no IntelliSense.

![opção Mostrar itens de importação](media/show-import-items.png)

## <a name="usage"></a>Uso

Depois de habilitar **Mostrar itens de importação**, o processo de usar o recurso para importar um item é semelhante às ações normais no IntelliSense. À medida que você digita o código, os itens que são válidos preencherão a lista de conclusão. Isso inclui itens que ainda não foram importados. Os itens que não são importados mostrarão seu namespace completo à direita do item, permitindo que você veja quais importações você está recebendo em seu projeto.

![Mostrar lista de itens de importação](media/show-import-items-list.png)

Na lista do IntelliSense, os namespaces são mostrados ao lado de membros que não são referenciados atualmente por uma `using` instrução. Se você escolher um desses itens na lista, o membro será adicionado ao seu código _e_ a `using` instrução será adicionada à parte superior do arquivo. Os membros de tipos já referenciados no código não mostrarão seu namespace no IntelliSense.

## <a name="see-also"></a>Confira também

- [Ações rápidas (Visual Studio no Windows)](/visualstudio/ide/quick-actions)
- [Refatorar o código (Visual Studio no Windows)](/visualstudio/ide/refactoring-in-visual-studio)
