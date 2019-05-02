---
title: Gerar campo, propriedade, variável local
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a8373339f921c032e52c00b5c8a54e910e5a1c54
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790323"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Gerar um campo, uma propriedade ou uma variável local no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** Permite gerar imediatamente o código para um campo, uma propriedade ou um local não declarado anteriormente.

**Quando:** Você introduz um novo campo, uma propriedade ou um local durante a digitação e deseja declará-lo correta e automaticamente.

**Por que:** Você pode declarar o campo, a propriedade ou o local antes de usá-lo; no entanto, essa funcionalidade gerará a declaração ou o tipo automaticamente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica um campo, um local ou uma propriedade que ainda não existe.

   - C#:

       ![Código em C# realçado](media/field-highlight-cs.png)

   - Visual Basic:

       ![Código em VB realçado](media/field-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![lâmpada de erro](media/error-bulb.png) ícone que aparece.
      - Clique no ícone de ![lâmpada de erro](media/error-bulb.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha com o rabisco vermelho.

      ![Visualização da geração de campo/propriedade/local](media/field-preview-cs.png)

3. Selecione uma das opções de geração no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   O campo, a propriedade ou o local é criado, com o tipo inferido de seu uso.

   - C#:

       ![Gerar o resultado do método C#](media/field-result-cs.png)

   - Visual Basic:

       ![Gerar o resultado do método VB](media/field-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)