---
title: 'IDebugDocumentHost:: GetFileName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetFileName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff2ad2e4ab419f1e503da072aaa550f3cb7cf0e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569398"
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Retorna o nome do documento sem informações de caminho.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrShortName`  
 fora Uma cadeia de caracteres que contém o nome curto do documento.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o nome curto do documento sem informações de caminho. O nome curto normalmente é usado em situações como a caixa de diálogo **salvar como...** .  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHost Interface](../../winscript/reference/idebugdocumenthost-interface.md)