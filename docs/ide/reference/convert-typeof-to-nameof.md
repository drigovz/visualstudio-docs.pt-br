---
title: Converter typeof em nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400318"
---
# <a name="convert-typeof-to-nameof"></a>Converter `typeof` em `nameof`

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O que:** Permite converter uma instância do `typeof(<QualifiedType>).Name` para `nameof(<QualifiedType>)` em C# e uma instância de `GetType(<QualifiedType>).Name` para `NameOf(<QualifiedType>)` no Visual Basic.

**Quando:**  Todas as instâncias de `typeof(<QualifiedType>).Name` onde `someType` não é um tipo genérico. Essa exclusão é necessária porque esse caso não retorna o mesmo valor de cadeia de caracteres que `nameof(<QualifiedType>)` . O mesmo é verdadeiro para a instância de Visual Basic.

**Por que:** Usar, `nameof` em vez do nome do `type` , evita a reflexão envolvida na recuperação de um `type` objeto e é uma maneira mais pragmática de escrevê-lo.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor dentro da `typeof(<QualifiedType>).Name` instância do C# ou `GetType(<QualifiedType>).Name` no Visual Basic.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecione uma das seguintes opções:

    - C#
      <br>Selecione **converter ' typeof ' para ' nameof '** : ![ Convert typeof em nameof](media/convert-type-of.PNG)

    - Visual Basic
      <br>Selecione **converter ' GetType ' em ' NameOf '** : ![ Convert typeof em NameOf](media/convert-get-type.PNG)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
