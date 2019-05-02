---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95b94dca9ef948a07b5c6458a9c8c53c8612eddd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920159"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Retorna informações que permite a construção de uma mensagem de erro legível por humanos.

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

#### <a name="parameters"></a>Parâmetros
 `pMessageType`

 [out] Retorna um valor da [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeração, que descreve o tipo de mensagem.

 `pbstrErrorFormat`

 [out] O formato da mensagem para o usuário final (consulte "Comentários" para obter detalhes).

 `hrErrorReason`

 [out] O código de erro, a mensagem é sobre.

 `pdwType`

 [out] Severidade do erro (usar constantes para MB_XXX `MessageBox`; por exemplo, `MB_EXCLAMATION` ou `MB_WARNING`).

 `pbstrHelpFileName`

 [out] Caminho para um arquivo de Ajuda (definido como um valor nulo se não houver nenhum arquivo de Ajuda).

 `pdwHelpId`

 [out] ID do tópico da Ajuda para exibir (definido como 0 se não houver nenhum tópico da Ajuda).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A mensagem de erro deve ser formatada ao longo das linhas de `"What I was doing.  %1"`. O `"%1"` , em seguida, deve ser substituído pelo chamador com a mensagem de erro derivada do código de erro (que é retornado no `hrErrorReason`). O `pMessageType` parâmetro informa ao chamador como a mensagem de erro final deve ser exibida.

## <a name="see-also"></a>Consulte também
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)