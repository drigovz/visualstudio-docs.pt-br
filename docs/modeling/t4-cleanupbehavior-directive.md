---
title: Diretiva CleanUpBehavior T4
description: Saiba mais sobre a diretiva CleanUpBehavior e como excluir o appDomain depois de processar um modelo de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c07d0bf714d42cc605d76d593ed48a70b925483
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363673"
---
# <a name="t4-cleanupbehavior-directive"></a>Diretiva CleanUpBehavior T4

Para excluir o appDomain depois de processar um modelo de texto, inclua a seguinte linha:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Os modelos de texto são processados em um appDomain que é separado do processo do host. Na maioria dos casos, quando um modelo de texto é processado, o appdomain é usado novamente para processar o próximo modelo. Mas se você especificar CleanupBehavior, o appDomain será excluído e o próximo modelo será processado em um novo appDomain.

Isso reduz o processamento de texto, mas pode ser útil para garantir que os recursos sejam descartados.

Essa diretiva só funciona no host do Visual Studio.
