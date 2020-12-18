---
title: Alterar a tecla de ajuda F1
description: Descreve como remapear ou remover o mapeamento de tecla F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jillfra
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: d9add6996949a97d6140ab6d063f13e02b677e79
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684086"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Alterar a tecla de ajuda F1 no Visual Studio

Se você quiser usar a tecla F1 para uma função diferente do serviço de ajuda F1 ou se apenas quiser desabilitar a ajuda usando F1, poderá remover ou modificar o mapeamento de chave.

> [!IMPORTANT]
> Se você quiser desabilitar a ajuda F1 devido a problemas de desempenho, é recomendável modificar o mapeamento de chave temporariamente para que você possa testar melhorias no serviço de ajuda F1 em atualizações para o Visual Studio. Na maioria dos cenários, F1 é uma maneira fácil de abrir páginas de referência para palavras-chave de idioma e APIs do editor de códigos, ou para abrir páginas de ajuda associadas a elementos do Windows ou da interface do usuário no IDE. Se você desabilitá-lo, desabilite-o para todos os usos de dentro do Visual Studio.

**Para desabilitar a ajuda F1:**

1. No Visual Studio, selecione   >  **Opções** de ferramentas e, em **ambiente**, selecione **teclado**.

1. Na caixa de texto **Mostrar comandos que contêm** , digite **help. F1** para filtrar a exibição de comandos.

   ![Desabilitar ajuda F1](../not-in-toc/media/disable-f1-help-key.png)

1. Selecione **remover** para remover o mapeamento de chave.

1. Selecione a caixa de texto **pressionar tecla de atalho** .

1. No teclado, pressione uma nova combinação de tecla ou chave para a ajuda F1, como **ALT + F1**, selecione **atribuir** e, em seguida, selecione **OK**.

Para obter mais informações sobre como configurar atalhos de teclado, consulte [identificar e personalizar atalhos de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
