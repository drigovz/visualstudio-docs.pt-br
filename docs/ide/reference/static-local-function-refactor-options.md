---
title: Refatoração de função local estática
ms.date: 09/28/2019
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: adbf84b9ae7566cd5e58a7c757ce09a37252b754
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782275"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refatoração de função local estática e ações rápidas

Este artigo descreve dois recursos de produtividade relacionados a funções locais estáticas. Uma é uma refatoração que torna uma função local estática e a outra é uma ação rápida que gera código para passar variáveis em uma função local estática.

## <a name="make-local-function-static"></a>Tornar a função local estática

Esta refatoração aplica-se a:

- C#

**O que:** Torna uma função local estática e passa em variáveis definidas fora da função para a declaração e as chamadas da função.

**Quando:** Você deseja que sua função local seja estática e que todas as variáveis sejam definidas no escopo da função.

**Por que:** As funções locais estáticas aprimoram a legibilidade: saber que o código específico é isolado torna mais fácil entender, ler e reutilizar. As funções locais estáticas também fornecem o escopo para evitar poluir uma classe com uma função estática que é chamada apenas em um único método.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre o nome da função local.

2. Pressione **Ctrl**+ **.** (ponto) para disparar o menu **ações rápidas e refatorar** .

   ![Tornar a função local estática](media/make-local-function-static.png)

3. Selecione **tornar a função local ' estática '.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passar variável explicitamente em uma função local estática

Esta ação rápida se aplica a:

- C#

**O que:** Passa uma variável explicitamente para uma função estática local.

**Quando:** Você deseja que uma função local seja estática, mas ainda use variáveis inicializadas fora dela.

**Por que:** O uso de funções locais estáticas fornece esclarecimentos aos leitores porque eles sabem que ele só pode ser declarado e chamado em um contexto específico do programa. Ele fornece a flexibilidade para definir variáveis fora deste contexto, mas ainda pode passá-las como argumentos para a função local estática.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor na variável em que ele é usado na função local estática.

2. Pressione **Ctrl**+ **.** (ponto) para disparar o menu **ações rápidas e refatorar** .

   ![Variável pass explicitamente na função local estática](media/pass-variable-explicitly-static-local-function.png)

3. Selecione **Passar variável explicitamente na função estática local**.

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)