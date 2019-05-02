---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
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
ms.openlocfilehash: 3e5800a6de15d2d59208022fa44d3c2f4c931e14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446574"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Retorna um intervalo de caracteres que foram adicionados usando o `IDebugDocumentHelper::AddDeferredText` método, no documento de host original.  
  
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
 [in] Cookie definido pelo host que representa a posição inicial do texto.  
  
 `pcharText`  
 [no, out] Um buffer de caracteres de texto. Esse método não retorna caracteres se esse parâmetro for `NULL`.  
  
 `pstaTextAttr`  
 [no, out] Um buffer de atributo de caracteres. Esse método não retorna atributos se esse parâmetro for `NULL`.  
  
 `pcNumChars`  
 [no, out] Indica o número real de caracteres/atributos retornados. Esse parâmetro deve ser definido como zero antes de chamar esse método.  
  
 `cMaxChars`  
 [in] O número máximo de caracteres a serem retornados.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método pode retornar `E_NOTIMPL`, se o host não chama `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Esse método retorna o texto do documento original. O host não manter o controle de edições ou outras alterações no documento.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)