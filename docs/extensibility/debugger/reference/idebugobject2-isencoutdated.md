---
title: 'IDebugObject2:: IsEncOutdated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90ff97b87ec2abaab87dfece5b2a2ac1cabb28c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726109"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Este método determina se o status editar e continuar deste objeto ou do contêiner pai está desatualizado. Um avaliador de expressão personalizado não implementa esse método e sempre retorna `E_NOTIMPL` .

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parâmetros
`pfEncOutdated`\
fora Diferente de zero ( `TRUE` ) se o estado editar e continuar estiver desatualizado, zero ( `FALSE` ) se não for.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

> [!NOTE]
> Um avaliador de expressão personalizado sempre deve retornar `E_NOTIMPL` .

## <a name="see-also"></a>Confira também
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
