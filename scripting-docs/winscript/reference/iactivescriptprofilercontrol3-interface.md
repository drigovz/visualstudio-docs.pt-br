---
title: Interface IActiveScriptProfilerControl3 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bebe351608b3136ac00a059bffab3535141e7fca
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097130"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>Interface IActiveScriptProfilerControl3
Fornece um método para enumerar os objetos de heap de GC associados a um mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>Métodos  
 [Método IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Retorna uma interface ([IActiveScriptProfilerHeapEnum Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que pode ser usado para iterar sobre os objetos de heap de GC no contexto do mecanismo de script associado.