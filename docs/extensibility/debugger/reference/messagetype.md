---
title: TIPO DE MENSAGEM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714492"
---
# <a name="messagetype"></a>MESSAGETYPE
Especifica o tipo de mensagem e a razão.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Campos
 `MT_OUTPUTSTRING`\
 Indica que a mensagem deve ser enviada para a janela de saída. Isto é mutuamente exclusivo de `MT_MESSAGEBOX`.

 `MT_MESSAGEBOX`\
 Indica que a mensagem deve ser mostrada em uma caixa de mensagem. Isto é mutuamente exclusivo de `MT_OUTPUTSTRING`.

 `MT_TYPE_MASK`\
 Um valor de máscara para isolar o destino da mensagem.

 `MT_REASON_EXCEPTION`\
 Indica que uma caixa de mensagem está sendo mostrada como resultado de uma exceção. Isto é mutuamente exclusivo de `MT_REASON_TRACEPOINT`.

 `MT_REASON_TRACEPOINT`\
 Indica que uma caixa de mensagem está sendo mostrada como resultado de atingir um ponto de rastreamento. Isto é mutuamente exclusivo para `MT_REASON_EXCEPTION`.

 `MT_REASON_MASK`\
 Um valor de máscara para isolar a razão da mensagem que está sendo mostrada.

## <a name="remarks"></a>Comentários
 Esses valores são retornados dos métodos [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage.](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

 Um dos valores da razão pode ser combinado com um `OR`dos valores de destino de saída usando um pouco .

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
