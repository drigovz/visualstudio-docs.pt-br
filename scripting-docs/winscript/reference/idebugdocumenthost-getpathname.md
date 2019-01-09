---
title: IDebugDocumentHost::GetPathName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5c33844ade2367ffeb7690306a5febbabde2f016
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096025"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Retorna o nome de arquivo e caminho completo do arquivo de origem do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrLongName`  
 [out] Uma cadeia de caracteres que contém o nome longo.  
  
 `pfIsOriginalFile`  
 [out] Um sinalizador que será true se `pbstrLongName` refere-se com o arquivo original para o documento, e false caso contrário.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Nenhum arquivo de origem pode ser criado ou determinado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o nome de arquivo e caminho completo do arquivo de origem do documento.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHost Interface](../../winscript/reference/idebugdocumenthost-interface.md)