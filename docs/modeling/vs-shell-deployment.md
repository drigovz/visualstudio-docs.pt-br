---
title: Implantação do VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934310"
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell

Um shell isolado permite que você determine quais Visual Studio funcionalidade que você precisa interagir com sua linguagem específica do domínio e como essa solução deve ser exibidos. Para obter mais informações sobre o shell isolado do Visual Studio, consulte [personalizar o Shell isolado](https://vspartner.com/pages/vsshells).

Para definir um Shell do Visual Studio como o destino de implantação:

1. No **DslPackage** projeto, abra **source.extension.tt**.

2. Sob `<SupportedProducts>` inserir:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Substitua *MyIsolatedShell* com o nome do seu pacote de shell isolado.