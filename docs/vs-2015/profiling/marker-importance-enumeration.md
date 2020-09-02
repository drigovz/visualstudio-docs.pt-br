---
title: Enumeração de marker_importance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198387"
---
# <a name="marker_importance-enumeration"></a>Enumeração marker_importance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Representa o nível de importância de um marcador da Visualização Simultânea.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Name|Descrição|  
|----------|-----------------|  
|`critical_importance`|Especifica que o marcador tem importância crítica.|  
|`high_importance`|Especifica que o marcador tem alta importância.|  
|`low_importance`|Especifica que o marcador tem baixa importância.|  
|`normal_importance`|Especifica que o marcador tem importância normal.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Consulte Também  
 [Namespace de diagnóstico](../profiling/diagnostic-namespace.md)
