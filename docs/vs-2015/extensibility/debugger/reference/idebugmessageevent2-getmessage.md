---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e571a7ba2116c093f8d4e4afd78fffc5014ae906
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922798"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém a mensagem a ser exibida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pMessageType`  
 [out] Retorna um valor da [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeração que descreve o tipo da mensagem.  
  
 `pbstrMessage`  
 [out] Retorna a mensagem.  
  
 `pdwType`  
 [out] Retorna o tipo da mensagem, usando as convenções do Win32 `MessageBox` função. Consulte a [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) função para obter detalhes.  
  
 `pbstrHelpFileName`  
 [no, out] Retorna o nome do arquivo de Ajuda. Pode ser um null (C++) ou valor vazio (C#), se não houver nenhum arquivo de Ajuda.  
  
 `pdwHelpId`  
 [no, out] Retorna o identificador de Ajuda. Pode ser 0 se não houver nenhuma ajuda associado com esta mensagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)
