---
title: Adicionar atributo DebuggerDisplay
description: Saiba como adicionar o atributo DebuggerDisplay para controlar como a janela variável do depurador exibe um objeto, uma propriedade ou um campo.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2166f7876909f62d9d16a2a6d5ec126d4544193e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956718"
---
# <a name="add-debuggerdisplay-attribute"></a>Adicionar atributo DebuggerDisplay

Esta geração de código aplica-se a:

- C#

**O que:** O [atributo DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) controla como um objeto, uma propriedade ou um campo é exibido nas janelas da variável do depurador.

**Quando:** Você deseja [fixar as propriedades](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) no depurador programaticamente no seu código.

**Por que:** As propriedades de fixação permitem que você inspecione rapidamente os objetos por suas propriedades, lendo a propriedade na parte superior da lista de propriedades do objeto dentro do depurador. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em um tipo, representante, propriedade ou campo. 

2. Pressione **Ctrl** + **.** para disparar o menu **ações rápidas e refatorar** e selecione **Adicionar atributo DebuggerDisplay**.

    ![Gerar Operadores de Comparação](media/add-debugger-display-attribute.png)

3. O atributo DebuggerDisplay será adicionado junto com um método auto que retorna o ToString padrão (). 

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)