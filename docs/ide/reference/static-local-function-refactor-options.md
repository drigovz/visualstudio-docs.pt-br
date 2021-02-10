---
title: Opções de refatoração de função local estática
description: Saiba como usar o menu ações rápidas e refatoração para tornar uma função local estática e passar variáveis definidas fora da função para a declaração e as chamadas da função.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 050ce5e90d9141892ff65602ca560d0add83da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967183"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refatoração de função local estática e ações rápidas

Este artigo descreve dois recursos de produtividade relacionados a funções locais estáticas. Uma é uma refatoração que torna uma função local estática e a outra é uma ação rápida que gera código para passar variáveis em uma função local estática.

## <a name="make-local-function-static"></a>Tornar local a função estática

Esta refatoração aplica-se a:

- C#

**O que:** Torna uma função local estática e passa em variáveis definidas fora da função para a declaração e as chamadas da função.

**Quando:** Você deseja que sua função local seja estática e que todas as variáveis sejam definidas no escopo da função.

**Por que:** As funções locais estáticas aprimoram a legibilidade: saber que o código específico é isolado torna mais fácil entender, ler e reutilizar. As funções locais estáticas também fornecem o escopo para evitar poluir uma classe com uma função estática que é chamada apenas em um único método.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre o nome da função local.

2. Pressione **Ctrl** + **.** (ponto) para disparar o menu **ações rápidas e refatorar** .

   ![Tornar local a função estática](media/make-local-function-static.png)

3. Selecione **tornar a função local ' estática '.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passar variável explicitamente em uma função local estática

Esta ação rápida se aplica a:

- C#

**O que:** Passa uma variável explicitamente para uma função estática local.

**Quando:** Você deseja que uma função local seja estática, mas ainda use variáveis inicializadas fora dela.

**Por que:** O uso de funções locais estáticas fornece esclarecimentos aos leitores porque eles sabem que ele só pode ser declarado e chamado em um contexto específico do programa. Ele fornece a flexibilidade para definir variáveis fora deste contexto, mas ainda pode passá-las como argumentos para a função local estática.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor na variável em que ele é usado na função local estática.

2. Pressione **Ctrl** + **.** (ponto) para disparar o menu **ações rápidas e refatorar** .

   ![Variável pass explicitamente na função local estática](media/pass-variable-explicitly-static-local-function.png)

3. Selecione **Passar variável explicitamente na função estática local**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)