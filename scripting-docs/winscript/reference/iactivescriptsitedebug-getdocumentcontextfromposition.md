---
title: IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df6c59fea5cfd60b6ae9a1b34e7000bd38dd9920
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992546"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
Usado pelo mecanismo de linguagem para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSourceContext`  
 [in] O conteúdo de origem conforme fornecido para `ParseScriptText` ou `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Caractere de deslocamento relativo ao início do bloco de script ou o scriptlet.  
  
 `uNumChars`  
 [in] Número de caracteres nesse contexto.  
  
 `ppsc`  
 [out] O contexto do documento correspondente a esse intervalo de posição do caractere.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Mecanismos de linguagem usam esse método para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)