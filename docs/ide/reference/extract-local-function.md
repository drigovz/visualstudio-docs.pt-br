---
title: Extrair função local
description: Transforme um fragmento de código em sua própria função selecionando o código e digitando Ctrl + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860965"
---
# <a name="extract-local-function-refactoring"></a>Extrair refatoração de função local

Esta refatoração aplica-se a:

- C#

**O que:** Permite transformar um fragmento de código de um método existente em uma função local.

**Quando:** Você tem um fragmento de código existente em algum método que precisa ser chamado a partir de uma função local.

**Por quê:** você poderia copiar/colar esse código, mas que poderia levar à eliminação de duplicação. Uma solução melhor é refatorar o fragmento em sua própria função local.

## <a name="how-to"></a>Como fazer

1. Realce o código a ser extraído.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**. 

3. Selecione **Extrair função local**.

    ![Captura de tela da janela do Visual Studio Code com uma linha realçada. O menu ações rápidas e refatoração é aberto e a função local de extração é selecionada.](media/extract-local-function.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
