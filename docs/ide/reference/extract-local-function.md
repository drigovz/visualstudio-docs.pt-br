---
title: Extrair função local
description: Transforme um fragmento de código em seu próprio método selecionando o código e digitando Ctrl + R, Ctrl + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515326"
---
# <a name="extract-local-function-refactoring"></a>Extrair refatoração de função local

Esta refatoração aplica-se a:

- C#

**O que é isso?** Permite transformar um fragmento de código de um método existente em uma função local.

**Quando:** Você tem um fragmento de código existente em algum método que precisa ser chamado de uma função local.

**Por quê:** você poderia copiar/colar esse código, mas que poderia levar à eliminação de duplicação. Uma solução melhor é refatorar esse fragmento em sua própria função local.

## <a name="how-to"></a>Como fazer

1. Destaque o código a ser extraído.

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**. 

3. Selecione **Extrair função local**.

    ![Extrair função local](media/extract-local-function.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
