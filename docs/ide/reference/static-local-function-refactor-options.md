---
title: Opções de refatoração de função local estática
ms.date: 02/10/2020
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
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144830"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refatorações de funções locais estáticas e ações rápidas

Este artigo descreve dois recursos de produtividade relacionados com funções locais estáticas. Um é um refatoração que torna uma função local estática, e o outro é uma Ação Rápida que gera código para passar variáveis em uma função local estática.

## <a name="make-local-function-static"></a>Tornar local a função estática

Esta refatoração aplica-se a:

- C#

**O que é isso?** Faz uma função local estática e passa em variáveis definidas fora da função para a declaração e chamadas da função.

**Quando:** Você quer que sua função local seja estática e que todas as variáveis sejam definidas no escopo da função.

**Por que:** As funções locais estáticas melhoram a legibilidade: saber que o código específico é isolado facilita a compreensão, a releitura e a reutilização. Funções locais estáticas também fornecem escopo para evitar poluir uma classe com uma função estática que é chamada apenas em um único método.

### <a name="how-to"></a>Como fazer

1. Coloque seu cuidador no nome da função local.

2. Pressione **Ctrl**+**.** (período) para ativar o menu **Ações Rápidas e Refatorações.**

   ![Tornar local a função estática](media/make-local-function-static.png)

3. Selecione **Fazer função local 'estática'.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passar variável explicitamente em uma função local estática

Esta Ação Rápida se aplica a:

- C#

**O que é isso?** Passa uma variável explicitamente para uma função estática local.

**Quando:** Você quer que uma função local seja estática, mas ainda use variáveis inicializadas fora dela.

**Por que:** O uso de funções estáticas locais presta esclarecimentos aos leitores porque eles sabem que ele só pode ser declarado e chamado em um contexto específico do programa. Ele fornece a flexibilidade para definir variáveis fora desse contexto, mas ainda ser capaz de passá-las como argumentos para a função local estática.

### <a name="how-to"></a>Como fazer

1. Coloque seu cuidador na variável onde ele é usado na função local estática.

2. Pressione **Ctrl**+**.** (período) para ativar o menu **Ações Rápidas e Refatorações.**

   ![Passar variável explicitamente em função local estática](media/pass-variable-explicitly-static-local-function.png)

3. Selecione **Passar variável explicitamente na função estática local**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)