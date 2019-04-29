---
title: Enumeração PROFILER_HEAP_ENUM_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d613ed3bcb4699f20d521f08b6c34d55d8363ba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830351"
---
# <a name="profilerheapenumflags-enumeration"></a>Enumeração PROFILER_HEAP_ENUM_FLAGS
Sinalizadores que representam se informações extras sobre um objeto de heap apontado em uma relação de objeto são expostos. Usado na [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Esse objeto de pilha não expõe informações adicionais sobre uma relação de objeto. Esse objeto de pilha se comporta da mesma forma como [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Esse objeto de pilha exporá informações sobre ou não um objeto apontado em uma relação de objeto é um método getter ou setter. Essas informações serão armazenadas em 2 bytes superiores (16 bits) do [profiler_heap_object_relationship](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo como um dos [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) valores de enumeração.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Esse objeto de heap é usado para exibir a subcadeia de caracteres corretamente.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Esse objeto de heap é usado para exibir a subcadeia de caracteres corretamente.|