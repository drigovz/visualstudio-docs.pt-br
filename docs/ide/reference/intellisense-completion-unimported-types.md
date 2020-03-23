---
title: Preenchimento do IntelliSense para tipos não importados
description: Como usar o preenchimento do IntelliSense para tipos que você ainda não importou com uma diretiva `using`.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094246"
---
# <a name="intellisense-completion-for-unimported-types"></a>Preenchimento do IntelliSense para tipos não importados

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** O IntelliSense fornece a conclusão para tipos não importados.

**Quando:** Você deseja adicionar um tipo que já tenha uma dependência em seu projeto, mas a declaração de importação ainda não foi adicionada ao seu arquivo. 

**Por que:** Você não precisa adicionar manualmente a declaração de importação ao seu arquivo.

## <a name="how-to"></a>Como fazer

1. Depois de começar a usar um tipo que tem uma dependência em seu projeto, o IntelliSense fornecerá sugestões.
2. Pressione **guia**. 

   A instrução import será adicionada ao seu arquivo.

   ![Preenchimento do IntelliSense para tipos não importados](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
