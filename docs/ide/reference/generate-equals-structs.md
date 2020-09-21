---
title: Gerar operadores IEquatable para structs
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5ee695169f52036858fc70598f81f375638ab03f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808110"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Gerar operadores IEquatable ao gerar Equals para structs

Esta geração de código aplica-se a:

- C#

**O que:** Permite gerar operadores **Equals** e **IEquatable** para [structs](/dotnet/csharp/language-reference/builtin-types/struct).

**Quando:** Você tem uma estrutura que adicionaremos automaticamente o IEquatable, bem como os operadores Equals e not Equals para você.

**Por**

- Se você estiver implementando um tipo de valor, considere substituir o método **Equals** para aumentar desempenho em relação à implementação padrão do método Equals em ValueType.

- Implementar a interface IEquatable implementa um método Equals () específico do tipo.

## <a name="how-to"></a>Instruções

1. Coloque o cursor em algum lugar na linha da sua declaração de struct.

2. Depois, siga um destes procedimentos:

   - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.

   - Clique no ícone ![chave de fenda](../media/screwdriver-icon.png) ícone que aparece na margem esquerda.

   ![Gerar IEquatable e Equals para structs](media/generate-equals-structs.png)

3. Selecione **gerar Equals (Object)** no menu suspenso.

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)