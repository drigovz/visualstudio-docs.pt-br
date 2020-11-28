---
title: Converter uma função local em um método
description: Saiba como usar o menu ações rápidas e refatoração para converter uma função local em um método.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 64a46fc6221f00e6bb130be8010cb2544a00dcc8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305566"
---
# <a name="convert-a-local-function-to-a-method"></a>Converter uma função local em um método

Esta refatoração aplica-se a:

- C#

**O que:** Converta uma função local em um método.

**Quando:** Você tem uma função local que deseja definir fora do seu contexto local atual.

**Por que:** Você deseja converter uma função local em um método para que você possa chamá-la fora do contexto local. O recomendado é converter em um método quando a função local está ficando muito longa. Ao definir a função em um método separado, seu código fica mais fácil de ler.

## <a name="convert-local-function-to-method-refactoring"></a>Refatoração de converter uma função local em um método

1. Coloque o cursor na função local.

    ![Converter uma função local em um exemplo de código de método](media/convert-local-function-to-method.png)

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Converter uma função local em um exemplo de correção de código de método](media/convert-local-function-to-method-codefix.png)

2. Pressione Enter para aceitar a refatoração.

    ![Converter a função local para um exemplo de resultado de método](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
