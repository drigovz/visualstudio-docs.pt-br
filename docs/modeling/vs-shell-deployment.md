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
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955668"
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