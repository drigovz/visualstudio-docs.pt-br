---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 809c63fe536166efe0779cd4e4dc0149b219390a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686048"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Especifica a condição associada com a contagem de passagem do ponto de interrupção que faz com que o ponto de interrupção seja acionado.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="members"></a>Membros
BP_PASSCOUNT_NONE não especifica nenhum estilo de contagem de passagem do ponto de interrupção.

BP_PASSCOUNT_EQUAL define o estilo de contagem de passagem de ponto de interrupção a ser igual. O ponto de interrupção é disparado quando o número de vezes que o ponto de interrupção é atingido é igual a contagem de passagem.

BP_PASSCOUNT_EQUAL_OR_GREATER define o estilo de contagem de passagem do ponto de interrupção para igual ou maior. O ponto de interrupção é disparado quando o número de vezes que o ponto de interrupção é atingido é igual ou maior que a contagem de passagem.

BP_PASSCOUNT_MOD Especifica uma contagem de aprovações de módulo. Por exemplo, se a contagem de passagem é do tipo `BP_PASSCOUNT_MOD` e o valor de contagem de passagem é 4, o ponto de interrupção é disparado sempre que a contagem de ocorrências for um múltiplo de 4.

## <a name="remarks"></a>Comentários
Usado para o `stylePassCount` membro do [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que por sua vez é um membro da estrutura a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
