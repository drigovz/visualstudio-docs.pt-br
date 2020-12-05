---
title: Gerar operadores IEquatable para structs
description: Saiba como usar o menu ações rápidas e refatoração para gerar operadores Equals e IEquatable para structs.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28d70c0ea95c9373eb87e6199d53f1b43fadd508
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617195"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Gerar operadores IEquatable ao gerar Equals para structs

Esta geração de código aplica-se a:

- C#

**O que:** Permite gerar operadores **Equals** e **IEquatable** para [structs](/dotnet/csharp/language-reference/builtin-types/struct).

**Quando:** Você tem uma estrutura que adicionaremos automaticamente o IEquatable, bem como os operadores Equals e not Equals para você.

**Por**

- Se você estiver implementando um tipo de valor, considere substituir o método **Equals** para aumentar desempenho em relação à implementação padrão do método Equals em ValueType.

- Implementar a interface IEquatable implementa um método Equals () específico do tipo.

## <a name="how-to"></a>Como fazer

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