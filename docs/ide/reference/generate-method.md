---
title: Gerar um método
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c85e3f849d7d74f326c1cf330b0e2c338d78fc6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668339"
---
# <a name="generate-a-method-in-visual-studio"></a>Gerar um método no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite que você adicione imediatamente um método a uma classe.

**Quando:** você introduz um novo método e deseja declará-lo correta e automaticamente.

**Por quê:** você poderia declarar o método e os parâmetros antes de usá-los; no entanto, esse recurso gerará a declaração automaticamente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica um método que ainda não existe.

   - C#:

       ![Código em C# realçado](media/method-highlight-cs.png)

   - Visual Basic:

       ![Código em VB realçado](media/method-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![lâmpada de erro](media/error-bulb.png) ícone que aparece.
      - Clique no ícone de ![lâmpada de erro](media/error-bulb.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha com o rabisco vermelho.

      ![Visualização de geração do método](media/method-preview-cs.png)

3. Selecione **Gerar método** no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   O método é criado com os parâmetros inferidos com base em seu uso.

   - C#:

       ![Gerar o resultado do método C#](media/method-result-cs.png)

   - Visual Basic:

       ![Gerar o resultado do método VB](media/method-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)