---
title: 'IDebugDocumentHost:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569287"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Retorna o caminho completo e o nome do arquivo de origem do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrLongName`  
 fora Uma cadeia de caracteres que contém o nome longo.  
  
 `pfIsOriginalFile`  
 fora Um sinalizador que será verdadeiro se `pbstrLongName` se referir ao arquivo original do documento; caso contrário, retornará false.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Nenhum arquivo de origem pode ser criado ou determinado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o caminho completo e o nome do arquivo de origem do documento.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHost Interface](../../winscript/reference/idebugdocumenthost-interface.md)