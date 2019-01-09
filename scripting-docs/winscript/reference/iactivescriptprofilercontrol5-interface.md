---
title: Interface IActiveScriptProfilerControl5 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b20afd05116a98e81a3eeea82e83e6ed200c44a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090812"
---
# <a name="iactivescriptprofilercontrol5-interface"></a>Interface IActiveScriptProfilerControl5
Fornece um método para enumerar os objetos de heap de GC associados a um mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>Métodos  
 [Método IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Retorna uma interface ([IActiveScriptProfilerHeapEnum Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que pode ser usado para iterar sobre os objetos de heap de GC no contexto do mecanismo de script associado.