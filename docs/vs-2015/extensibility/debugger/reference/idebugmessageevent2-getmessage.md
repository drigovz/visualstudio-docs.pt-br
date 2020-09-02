---
title: 'IDebugMessageEvent2:: GetMessage | Microsoft Docs'
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
ms.openlocfilehash: 14eb540962db3a806273d5c76facb7f9bf25dee7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685892"
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
 fora Retorna um valor da enumeração [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) que descreve o tipo da mensagem.  
  
 `pbstrMessage`  
 fora Retorna a mensagem.  
  
 `pdwType`  
 fora Retorna o tipo da mensagem, usando as convenções da função do Win32 `MessageBox` . Consulte a função [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) para obter detalhes.  
  
 `pbstrHelpFileName`  
 [entrada, saída] Retorna o nome do arquivo de ajuda. Pode ser um valor nulo (C++) ou vazio (C#) se não houver nenhum arquivo de ajuda.  
  
 `pdwHelpId`  
 [entrada, saída] Retorna o identificador da ajuda. Poderá ser 0 se não houver ajuda associada a esta mensagem.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)
