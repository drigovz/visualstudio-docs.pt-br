---
title: 'VsgDbg:: ~ VsgDbg (destruidor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d68b7dbf64f15b376cd49bdd2d60f507014f5167
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877855"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruidor)
Destrói uma instância da `VsgDbg` classe. Se informações de gráficos ativamente está sendo registradas, o arquivo de log de gráficos é finalizado e fechado, e os recursos que foram usados durante a captura ativamente informações gráficas são liberados.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Consulte também  
 [VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)