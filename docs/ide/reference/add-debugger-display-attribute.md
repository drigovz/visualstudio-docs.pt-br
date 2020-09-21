---
title: Adicionar atributo DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: db49bfd1672866a755cce6780527520da2cad420
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810383"
---
# <a name="add-debuggerdisplay-attribute"></a>Adicionar atributo DebuggerDisplay

Esta geração de código aplica-se a:

- C#

**O que:** O [atributo DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) controla como um objeto, uma propriedade ou um campo é exibido nas janelas da variável do depurador.

**Quando:** Você deseja [fixar as propriedades](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) no depurador programaticamente no seu código.

**Por que:** As propriedades de fixação permitem que você inspecione rapidamente os objetos por suas propriedades, lendo a propriedade na parte superior da lista de propriedades do objeto dentro do depurador. 

## <a name="how-to"></a>Instruções

1. Coloque o cursor em um tipo, representante, propriedade ou campo. 

2. Pressione **Ctrl** + **.** para disparar o menu **ações rápidas e refatorar** e selecione **Adicionar atributo DebuggerDisplay**.

    ![Gerar Operadores de Comparação](media/add-debugger-display-attribute.png)

3. O atributo DebuggerDisplay será adicionado junto com um método auto que retorna o ToString padrão (). 

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)