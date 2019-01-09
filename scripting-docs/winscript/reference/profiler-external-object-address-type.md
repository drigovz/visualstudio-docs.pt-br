---
title: Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9642a4a-f1fd-408a-9de6-e51562337bf1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ec2be5f35d15f0f7260e224b53ad4d8f07e8734
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086496"
---
# <a name="profilerexternalobjectaddress-type"></a>Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS
O endereço do objeto externo de um objeto, como um objeto alocado em C++, que está fora do heap de JavaScript. Usado na [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e [estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef void* PROFILER_EXTERNAL_OBJECT_ADDRESS;  
```