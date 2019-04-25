---
title: Introduzir variável local
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5564752fcecfe2d7a1b2d0bf7632a9cebe3d9353
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540960"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introduzir uma variável local no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** Permite gerar imediatamente uma variável local para substituir uma expressão existente.

**Quando:** Você tem um código que poderá ser reutilizado com facilidade posteriormente se ele estiver em uma variável local.

**Por que:** Você pode copiar e colar o código várias vezes para usá-lo em vários locais. No entanto, é melhor executar a operação uma vez, armazenar o resultado em uma variável local e usar a variável local durante todo o processo.

## <a name="how-to"></a>Como fazer

1. Realce a expressão que você deseja atribuir a uma nova variável local.

   - C#:

       ![Código em C# realçado](media/local-highlight-cs.png)

   - Visual Basic:

       ![Código em VB realçado](media/local-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Clique no ícone de ![chave de fenda](media/screwdriver.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha com a expressão realçada.

   ![Introduzir versão prévia local](media/local-preview-cs.png)

3. Selecione **Introduzir local para a (todas as ocorrências da) 'expressão'** no menu suspenso.

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