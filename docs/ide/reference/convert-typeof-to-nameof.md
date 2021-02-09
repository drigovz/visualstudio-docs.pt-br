---
title: Converter typeof em nameof
description: Saiba como usar o menu ações rápidas e refatoração no Visual Studio para converter typeof em nameof em C# e GetType em NameOf em Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919699"
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
      <br>Selecione **converter ' typeof ' para ' nameof '**: ![ captura de tela do menu ações rápidas e refatoração no Visual Studio com converter ' typeof ' em ' nameof ' selecionado e alterações de código em C# mostradas.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Selecione **converter ' GetType ' em ' NameOf '**: ![ captura de tela do menu ações rápidas e refatoração no Visual Studio com converter ' GetType ' em ' NameOf ' selecionado e Visual Basic alterações de código mostradas.](media/convert-get-type.PNG)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
