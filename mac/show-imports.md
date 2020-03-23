---
title: Mostrar itens de importação
description: Use itens de importação show para expandir o IntelliSense no Visual Studio para Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451506"
---
# <a name="show-import-items"></a>Mostrar itens de importação

Visual Studio for Mac pode mostrar todos os tipos disponíveis, mesmo que eles não sejam importados para o seu projeto, em sua lista de conclusão do IntelliSense. Ao selecionar um item que não é `using` importado, a declaração correta será adicionada ao seu arquivo de origem.

![mostrar visão geral dos itens de importação](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Como habilitar

Para habilitar esse recurso, abra **preferências** via **Visual Studio** > **Preferences** e navegue até **o Editor de** > Texto**IntelliSense**. Verifique a caixa **Mostrar itens de importação** para habilitar itens adicionais no IntelliSense.

![mostrar opção itens de importação](media/show-import-items.png)

## <a name="usage"></a>Uso

Uma vez habilitado **mostrar itens de importação,** o processo de usar o recurso para importar um item é semelhante às ações normais dentro do IntelliSense. À medida que você digita código, os itens válidos preencherão a lista de conclusão. Isso inclui itens que ainda não foram importados. Os itens que não são importados mostrarão seu espaço completo para a direita do item, permitindo que você veja quais importações você está puxando para o seu projeto.

![mostrar lista de itens de importação](media/show-import-items-list.png)

Na lista IntelliSense, os namespaces são mostrados ao lado `using` de membros que não são referenciados atualmente por uma declaração. Se você escolher um desses itens da lista, o membro _and_ será `using` adicionado ao seu código e a declaração será adicionada à parte superior do arquivo. Membros de tipos já referenciados no codificado não mostrarão seu namespace no IntelliSense.

## <a name="see-also"></a>Confira também

- [Ações rápidas (Visual Studio no Windows)](/visualstudio/ide/quick-actions)
- [Refatorar o código (Visual Studio no Windows)](/visualstudio/ide/refactoring-in-visual-studio)
