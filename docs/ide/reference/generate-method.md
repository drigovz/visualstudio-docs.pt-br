---
title: Gerar um método
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d815b638033e16796c90a362207b820bfe7cc57d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794762"
---
# <a name="generate-a-method-in-visual-studio"></a>Gerar um método no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** Permite adicionar imediatamente um método a uma classe.

**Quando:** Você introduz um novo método e deseja declará-lo correta e automaticamente.

**Por que:** Você pode declarar o método e os parâmetros antes de usá-los; no entanto, essa funcionalidade gerará a declaração automaticamente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica um método que ainda não existe.

   - C#:

       ![Código em C# realçado](media/method-highlight-cs.png)

   - Visual Basic:

       ![Código em VB realçado](media/method-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
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