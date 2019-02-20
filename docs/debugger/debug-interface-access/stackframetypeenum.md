---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dab674576655df3b4a695d97fdfdb42df2ffa449
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227258"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Especifica o tipo de quadro de pilha.

## <a name="syntax"></a>Sintaxe

```C++
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
Ponteiro de quadro especificado; Informações de FPO disponíveis.

`FrameTypeTrap`  
Quadro de interceptação de kernel.

`FrameTypeTSS`  
Quadro de interceptação de kernel.

`FrameTypeStandard`  
Quadro de pilha EBP padrão.

`FrameTypeFrameData`  
Ponteiro de quadro especificado; Informações de dados de quadro disponíveis.

`FrameTypeUnknown`  
Quadro que não tem nenhuma informação de depuração.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados por uma chamada para o [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
[Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
