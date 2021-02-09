---
title: Implantação do VS Shell
description: Saiba como um shell isolado permite determinar qual funcionalidade do Visual Studio você precisa para interagir com sua DSL e como essa solução deve ser exibida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924215"
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell

Um shell isolado permite que você determine qual funcionalidade do Visual Studio você precisa para interagir com sua linguagem específica de domínio e como essa solução deve ser exibida. Para obter mais informações sobre o Shell isolado do Visual Studio, consulte [Personalizando o Shell isolado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Para definir um shell do Visual Studio como o destino de implantação:

1. No projeto **DslPackage** , abra **Source.Extension.tt**.

2. Em `<SupportedProducts>` Inserir:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Substitua *MyIsolatedShell* pelo nome do seu pacote de shell isolado.