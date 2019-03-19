---
title: Script ativo Profiler constantes, enumerações e estruturas | Microsoft Docs
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
ms.openlocfilehash: 1d39e6feb2cddd0c573368db9bf50b1e77f2e48d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154719"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Constantes, enumerações e estruturas de criador de perfil do script ativo
As enumerações a seguir são usadas pelo Active Directory Interfaces do Profiler de Script.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, Enumerações e Estruturas  
  
|Constantes|Descrição|  
|---------------|-----------------|  
|[Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|O endereço do objeto externo do criador de perfil. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e [estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|A ID do objeto heap. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[estrutura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)e [Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|A ID do nome do objeto heap. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Enumerações|Descrição|  
|------------------|-----------------|  
|[Enumeração PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Indica os tipos de eventos que devem ser analisados.|  
|[Enumeração PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Sinalizadores que representam se informações extras sobre um objeto de heap apontado em uma relação de objeto são expostos. Usado na [método IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Enumeração PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Sinalizadores que representam informações básicas sobre o objeto de heap. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Enumeração PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Representa os diferentes tipos de informações opcionais. Usado na [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Enumeração PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Representa informações sobre o objeto na relação. Usado na [estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Enumeração PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Especifica o tipo de script.|  
  
|Estruturas|Descrição|  
|----------------|-----------------|  
|[Estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Representa os objetos da pilha coletados pelas [método IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Representa informações opcionais sobre objetos de heap.|  
|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Representa uma relação de um objeto de heap.|  
|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Representa uma lista de relações que pertencem a um objeto de heap.|  
|[Estrutura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Essa estrutura é associada a apenas os objetos de função. A lista de escopo representa o fechamento da função como uma lista de escopos, onde cada escopo é um objeto de heap com uma lista de propriedade associada que representa as variáveis em cada escopo fornecido. Em alguns casos, os nomes dos objetos no escopo podem não estar disponíveis, apenas suas ids.|  
|[Estrutura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Representa informações sobre o tipo da subcadeia de caracteres.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)