---
title: Estrutura PROFILER_HEAP_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c8682cd54b10144800f17cab3a8a03ea8169889
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093126"
---
# <a name="profilerheapobject-structure"></a>Estrutura PROFILER_HEAP_OBJECT
Representa os objetos da pilha coletados pelas [método IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Tipo|Descrição|  
|------------|----------|-----------------|  
|ObjectId|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|A ID do objeto heap.|  
|externalObjectAddress|[Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|O endereço do objeto externo de um objeto, como um objeto alocado em C++, que está fora do heap de JavaScript.|  
|typeNameId|[Tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|A ID do nome do tipo de objeto heap, recuperada do [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Somente um dos `externalObjectAddress` ou `typeName` estiver presente, dependendo o `flags` valor.|  
|sinalizadores|[Enumeração PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Os sinalizadores que contêm informações básicas sobre o objeto de heap.|  
|optionalInfoCount|USHORT|O número de [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) registros que estão disponíveis para o objeto de heap.|