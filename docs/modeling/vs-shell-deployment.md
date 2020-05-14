---
title: Implantação do VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444993"
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell

Um shell isolado permite determinar qual funcionalidade do Visual Studio você precisa para interagir com seu idioma específico de domínio e como essa solução deve aparecer. Para obter mais informações sobre o shell isolado do Visual Studio, consulte [Personalizando a Concha Isolada](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Para definir um Visual Studio Shell como alvo de implantação:

1. No projeto **DslPackage,** **abra source.extension.tt**.

2. Sob `<SupportedProducts>` a inserção:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Substitua *myisolatedshell* pelo nome do seu pacote shell isolado.
