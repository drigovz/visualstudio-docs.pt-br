---
title: Introduzir variável local
description: Gere imediatamente uma variável local para substituir uma expressão existente. Selecione a expressão, clique com o botão direito do mouse e selecione o menu Ações Rápidas e Refatorações, selecione Introduzir local para (todas as ocorrências da) 'expressão'.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 564ba133074af3749bd909f1b0a7fe32822f5d75
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833254"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introduzir uma variável local no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente uma variável local para substituir uma expressão existente.

**Quando:** você tiver um código que poderia ser facilmente reutilizado posteriormente se estivesse em uma variável local.

**Por quê:** você poderia copiar e colar o código várias vezes a fim de usá-lo em vários locais. No entanto, seria melhor executar a operação uma vez, armazenar o resultado em uma variável local e usar a variável local durante todo o processo.

## <a name="how-to"></a>Como fazer

1. Realce a expressão que você deseja atribuir a uma nova variável local.

   - C#:

       ![Código em C# realçado](media/local-highlight-cs.png)

   - Visual Basic:

       ![Código em VB realçado](media/local-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Clique no botão ![Captura de tela do ícone de chave de fenda que aparece na margem esquerda do menu ações rápidas e refatoração.](media/screwdriver.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha com a expressão realçada.

   ![Introduzir versão prévia local](media/local-preview-cs.png)

3. Selecione **introduzir local para (todas as ocorrências) de ' expressão '** no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   A variável local é criada, com o tipo inferido com base em seu uso. Forneça um novo nome à nova variável local.

   - C#:

       ![Resultado da implementação da interface em C#](media/local-result-cs.png)

   - Visual Basic:

       ![Resultado da implementação da interface em VB](media/local-result-vb.png)

   > [!NOTE]
   > É possível usar a opção de menu **...todas as ocorrências de...** para substituir todas as instâncias da expressão selecionada, não somente a que foi especificamente realçada.

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
