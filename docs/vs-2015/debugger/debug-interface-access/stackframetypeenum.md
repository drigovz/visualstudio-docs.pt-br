---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179197"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica o tipo de quadro de pilha.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elementos  
 `FrameTypeFPO`  
 Ponteiro de quadro omitido; Informações de FPO disponíveis.  
  
 `FrameTypeTrap`  
 Quadro de interceptação do kernel.  
  
 `FrameTypeTSS`  
 Quadro de interceptação do kernel.  
  
 `FrameTypeStandard`  
 Quadro de pilha EBP padrão.  
  
 `FrameTypeFrameData`  
 Ponteiro de quadro omitido; Informações de dados de quadro disponíveis.  
  
 `FrameTypeUnknown`  
 Quadro que não tem nenhuma informação de depuração.  
  
## <a name="remarks"></a>Comentários  
 Os valores nessa enumeração são retornados por uma chamada para o método [IDiaStackFrame:: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst. h  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
