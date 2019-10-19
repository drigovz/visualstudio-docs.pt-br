---
title: 'IDebugDocumentHost:: GetDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569429"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Retorna um intervalo de caracteres que foram adicionados usando o método `IDebugDocumentHelper::AddDeferredText`, no documento host original.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwTextStartCookie`  
 no Cookie definido pelo host que representa a posição inicial do texto.  
  
 `pcharText`  
 [entrada, saída] Um buffer de texto de caractere. Esse método não retornará caracteres se esse parâmetro for `NULL`.  
  
 `pstaTextAttr`  
 [entrada, saída] Um buffer de atributo de caractere. Esse método não retornará atributos se esse parâmetro for `NULL`.  
  
 `pcNumChars`  
 [entrada, saída] Indica o número real de caracteres/atributos retornados. Esse parâmetro deve ser definido como zero antes de chamar este método.  
  
 `cMaxChars`  
 no O número máximo de caracteres a serem retornados.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método pode retornar `E_NOTIMPL`, se o host não chamar `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Esse método retorna o texto do documento original. O host não mantém o controle das edições ou outras alterações no documento.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)