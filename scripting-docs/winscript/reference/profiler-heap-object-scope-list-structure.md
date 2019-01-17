---
title: Estrutura PROFILER_HEAP_OBJECT_SCOPE_LIST | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 114b1a55fce34908c4274877583164aff4ec8dba
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344818"
---
# <a name="profilerheapobjectscopelist-structure"></a>Estrutura PROFILER_HEAP_OBJECT_SCOPE_LIST
Essa estrutura é associada a apenas os objetos de função. A lista de escopo representa o fechamento da função como uma lista de escopos, onde cada escopo é um objeto de heap com uma lista de propriedade associada que representa as variáveis em cada escopo fornecido. Em alguns casos, os nomes de objetos no escopo não esteja disponível e apenas seu índice na lista de propriedades está disponível.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Tipo|Descrição|  
|------------|----------|-----------------|  
|count|UINT|O número de escopos|  
|escopos|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Uma matriz de escopos.|