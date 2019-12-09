---
title: Implantação do VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e010d2efd8174f2c61d7c97eb63d585f47812ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663667"
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell

Um shell isolado permite que você determine qual funcionalidade do Visual Studio você precisa para interagir com sua linguagem específica de domínio e como essa solução deve ser exibida. Para obter mais informações sobre o Shell isolado do Visual Studio, consulte [Personalizando o Shell isolado](https://vspartner.com/pages/vsshells).

Para definir um shell do Visual Studio como o destino de implantação:

1. No projeto **DslPackage** , abra **Source.Extension.tt**.

2. Em `<SupportedProducts>` inserir:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Substitua *MyIsolatedShell* pelo nome do seu pacote de shell isolado.