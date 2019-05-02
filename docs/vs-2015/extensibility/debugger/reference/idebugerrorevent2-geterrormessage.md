---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4b25e040fe391b0bfbd05159779096e6bad9951
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922389"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna informações que permite a construção de uma mensagem de erro legível por humanos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
