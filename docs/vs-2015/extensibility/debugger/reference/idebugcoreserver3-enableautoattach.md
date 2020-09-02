---
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45362c9456b99d6cec0af01dcb29844d02363a27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569754"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Habilita a anexação automática para os mecanismos de depuração especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rgguidSpecificEngines`  
 no Matriz de GUIDs para cada mecanismo de depuração a ser marcado como anexação automática.  
  
 `celtSpecificEngines`  
 no O número de mecanismos especificado em `rgguidSpecificEngines` .  
  
 `pszStartPageUrl`  
 no A URL inicial a ser usada ao anexar automaticamente.  
  
 `pbstrSessionID`  
 fora ID da sessão que foi anexada automaticamente.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro. Um código de erro é `E_AUTO_ATTACH_NOT_REGISTERED` , que indica que a fábrica de classes de anexação automática não foi registrada.  
  
## <a name="remarks"></a>Comentários  
 Quando um programa associado à URL especificada é iniciado, os mecanismos de depuração especificados são iniciados e anexados automaticamente.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
