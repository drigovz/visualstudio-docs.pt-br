---
title: Enumeração PROFILER_RELATIONSHIP_INFO | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808887"
---
# <a name="profilerrelationshipinfo-enumeration"></a>Enumeração PROFILER_RELATIONSHIP_INFO
Representa informações sobre o objeto na relação. Usado na [estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|O objeto é um número.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|O objeto é uma cadeia de caracteres.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|O objeto é um objeto de heap.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|O objeto é externo, ou seja, não no heap de coleta de lixo.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|O objeto é um BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|O objeto é uma subcadeia de caracteres.|