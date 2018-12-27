---
title: Implantação do VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 663e706dba9ec7b6479e3e9360ef8aa2d12b1400
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739491"
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