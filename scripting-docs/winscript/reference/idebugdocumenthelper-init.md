---
title: 'IDebugDocumentHelper:: init | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576857"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
O método `Init` Inicializa um auxiliar de documento de depuração com um nome e atributos iniciais.  
  
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
 no O aplicativo de depuração associado a este documento.  
  
 `pszShortName`  
 no Uma cadeia de caracteres terminada em nulo que contém o nome curto do documento.  
  
 `pszLongName`  
 no Uma cadeia de caracteres terminada em nulo que contém o nome longo do documento.  
  
 `docAttr`  
 no Especifica os atributos do documento de texto.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método inicializa um auxiliar de documento de depuração com um nome e atributos iniciais.  
  
 Este documento não aparecerá na árvore até que `IDebugDocumentHelper::Attach` seja chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHelper:: anexar](../../winscript/reference/idebugdocumenthelper-attach.md)    
 @No__t_1 de [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [TEXT_DOC_ATTR Constants](../../winscript/reference/text-doc-attr-constants.md)