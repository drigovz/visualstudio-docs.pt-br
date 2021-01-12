---
title: Extrair função local
description: Transforme um fragmento de código em sua própria função selecionando o código e digitando Ctrl + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129452"
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

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
