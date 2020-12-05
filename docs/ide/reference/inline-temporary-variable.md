---
title: Substituir uma variável temporária por seu valor
description: Saiba como usar o menu ações rápidas e refatoração para remover uma variável temporária e substituí-la pelo valor em seu lugar.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d24c63bdc1908ecc15c206faeda3e9de511f8f9b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617403"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Refatoração Embutir uma variável temporária

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite que você remova uma variável temporária e substitua-a pelo seu valor.

**Quando:** o uso da variável temporária dificulta o entendimento do código.

**Por quê:** remover uma variável temporária pode facilitar a leitura do código.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro de uma variável temporária para ser embutida:

   - C#:

       ![Código realçado – C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Código realçado – Visual Basic](media/inline-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse no código e selecione o menu **Ações e Refatorações Rápidas**.

3. Selecione **Variável temporária embutida** no pop-up da janela Visualização.

   A variável é removida e seus usos são substituídos pelo valor da variável.

   - C#:

      ![Resultado embutido – C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Resultado embutido – Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
