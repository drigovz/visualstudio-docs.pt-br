---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730037"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Retorna informações que permitem a construção de uma mensagem de erro legível por humanos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>parâmetros
`pMessageType`\
[fora] Retorna um valor da enumeração [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) descrevendo o tipo de mensagem.

`pbstrErrorFormat`\
[fora] O formato da mensagem final para o usuário (consulte "Observações" para obter detalhes).

`hrErrorReason`\
[fora] O código de erro da mensagem é sobre.

`pdwType`\
[fora] Gravidade do erro (use as para `MessageBox`MB_XXX; por `MB_EXCLAMATION` `MB_WARNING`exemplo, ou ).

`pbstrHelpFileName`\
[fora] Caminho para um arquivo de ajuda (definido como um valor nulo se não houver arquivo de ajuda).

`pdwHelpId`\
[fora] ID do tópico de ajuda a ser exibido (definido como 0 se não houver tópico de ajuda).

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A mensagem de erro deve `"What I was doing.  %1"`ser formatada ao longo das linhas de . O `"%1"` seria então substituído pelo chamador com a mensagem de erro derivada do código de erro (que é devolvido em `hrErrorReason`). O `pMessageType` parâmetro informa ao interlocutor como a mensagem de erro final deve ser exibida.

## <a name="see-also"></a>Confira também
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)
