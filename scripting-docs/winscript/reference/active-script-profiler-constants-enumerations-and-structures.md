---
title: Constantes, enumerações e estruturas do criador de perfil de script ativo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572685"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Constantes, enumerações e estruturas de criador de perfil do script ativo
As enumerações a seguir são usadas pelas interfaces do criador de perfil de script ativo.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, Enumerações e Estruturas  
  
|Constantes|Descrição|  
|---------------|-----------------|  
|[Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|O endereço do objeto externo do criador de perfil. Usado na estrutura [PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e na [estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|A ID do objeto de heap. Usado em estrutura de [PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)de estrutura[PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [estrutura de PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)e estrutura de [PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|A ID do nome do objeto de heap. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Enumerações|Descrição|  
|------------------|-----------------|  
|[Enumeração PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Indica os tipos de eventos que devem ser cujo perfil deve ser criado.|  
|[Enumeração PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Sinalizadores que representam se informações extras sobre um objeto de heap apontado em uma relação de objeto são expostas. Usado no [método IActiveScriptProfilerControl5:: EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Enumeração PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Sinalizadores que representam informações básicas sobre o objeto de heap. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Enumeração PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Representa tipos diferentes de informações opcionais. Usado na [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Enumeração PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Representa informações sobre o objeto na relação. Usado na [estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Enumeração PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Especifica o tipo de script.|  
  
|Estruturas|Descrição|  
|----------------|-----------------|  
|[Estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Representa os objetos de heap coletados pelo [método IActiveScriptProfilerControl3:: EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Representa informações opcionais sobre objetos de heap.|  
|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Representa uma relação de um objeto de heap.|  
|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Representa uma lista de relações que pertencem a um objeto heap.|  
|[Estrutura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Essa estrutura é associada somente a objetos de função. A lista escopo representa o fechamento da função como uma lista de escopos onde cada escopo é um objeto de heap com uma lista de propriedades associada que representa as variáveis em cada escopo determinado. Em alguns casos, os nomes de objetos nesse escopo podem não estar disponíveis, somente suas IDs.|  
|[Estrutura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Representa informações sobre o tipo da subcadeia de caracteres.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)