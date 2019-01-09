---
title: Enumeração PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78285f332b339533d81228de5877043f699a67c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096285"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>Enumeração PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Sinalizadores que representam se um objeto de heap apontado em uma relação de objeto é um método getter ou setter. Usado na [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) método quando o valor PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS for especificado no `enumFlags` parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Esse objeto de heap apontado em uma relação de objeto não for identificado como método de um getter ou setter.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|O objeto de heap apontado em uma relação de objeto é um método getter. Essas informações serão armazenadas em 2 bytes superiores (16 bits) do [profiler_heap_object_relationship](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|O objeto de heap apontado em uma relação de objeto é um método de setter. Essas informações serão armazenadas em 2 bytes superiores (16 bits) do `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` campo.|