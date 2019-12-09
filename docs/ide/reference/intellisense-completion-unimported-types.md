---
title: Preenchimento do IntelliSense para tipos não importados
description: Como usar o preenchimento do IntelliSense para tipos que você ainda não importou com uma diretiva `using`.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312924"
---
# <a name="intellisense-completion-for-unimported-types"></a>Preenchimento do IntelliSense para tipos não importados

Esta refatoração aplica-se a:

- C#

**O quê:** O IntelliSense oferece preenchimento para tipos não importados.

**Quando:** Você deseja adicionar um tipo que já tem uma dependência em seu projeto, mas a instrução import ainda não foi adicionada ao seu arquivo. 

**Por que:** Você não precisa adicionar manualmente a instrução de importação ao seu arquivo.

## <a name="how-to"></a>Como fazer

1. Depois de começar a usar um tipo que tem uma dependência em seu projeto, o IntelliSense fornecerá sugestões.
2. Pressione **Tab**. 

   A instrução import será adicionada ao seu arquivo.

   ![Preenchimento do IntelliSense para tipos não importados](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
