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
ms.openlocfilehash: 44f715c4f74d9b120b324e2d68417a24c9b42684
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602449"
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
`FrameTypeFPO` Ponteiro de quadro especificado; Informações de FPO disponíveis.

`FrameTypeTrap` Quadro de interceptação de kernel.

`FrameTypeTSS` Quadro de interceptação de kernel.

`FrameTypeStandard` Quadro de pilha EBP padrão.

`FrameTypeFrameData` Ponteiro de quadro especificado; Informações de dados de quadro disponíveis.

`FrameTypeUnknown` Quadro que não tem nenhuma informação de depuração.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados por uma chamada para o [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
