---
title: Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e5658f70e6a24151af75f4455fc44c2c756b9e9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091943"
---
# <a name="profilerheapobjectrelationship-structure"></a>Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP
Representa uma relação de um objeto de heap.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|relationshipId|[Tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|A ID do relacionamento com o nome da [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[Enumeração PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Informações sobre a relação.|  
|numberValue|double|O valor do número. Somente um dos `numberValue` / `stringValue` / `objectId` / `externalObjectAddress` definido, com base no `relationshipInfo` valor.|  
|"StringValue"|LPCWSTR|O valor da cadeia de caracteres.|  
|ObjectId|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|A ID do objeto heap.|  
|externalObjectAddress|[Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|O endereço do objeto externo.|  
|subcadeia de caracteres|[Estrutura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|As informações sobre o tipo de subcadeia de caracteres.|