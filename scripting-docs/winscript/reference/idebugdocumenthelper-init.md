---
title: 'Idebugdocumenthelper:: init | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4bcb64b7bbb1c61e7f031d872f7d1440fd17833
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086626"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
O `Init` método inicializa um auxiliar de documentos de depuração com um nome e atributos inicias.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pda`  
 [in] O aplicativo de depuração associado a este documento.  
  
 `pszShortName`  
 [in] Uma cadeia terminada em nulo que contém o nome curto do documento.  
  
 `pszLongName`  
 [in] Uma cadeia terminada em nulo que contém o nome longo do documento.  
  
 `docAttr`  
 [in] Especifica atributos de documento de texto.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método inicializa um auxiliar de documentos de depuração com um nome e atributos inicias.  
  
 Este documento não aparecem na árvore até `IDebugDocumentHelper::Attach` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [Idebugdocumenthelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR Constants](../../winscript/reference/text-doc-attr-constants.md)