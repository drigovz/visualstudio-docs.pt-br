---
title: 'IDispError:: GetHelpInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573126"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Retorna o caminho do arquivo de ajuda e a ID de contexto do tópico que explica o erro, se possível.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrFileName`  
 fora Cadeia de caracteres que contém o caminho totalmente qualificado do arquivo de ajuda. Se não houver nenhum arquivo de ajuda ou se ocorrer um erro, o valor de retorno será nulo.  
  
 `pdwContext`  
 fora A ID de contexto da ajuda para o erro. Se não houver nenhum arquivo de ajuda (se `pbstrFileName` for nulo), esse parâmetro não terá significado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Ocorreu um erro específico do provedor.|  
|`E_INVALIDARG`|`pbstrFileName` ou `pdwContext` era nulo.|  
|`E_OUTOFMEMORY`|O provedor não pôde alocar memória suficiente para retornar o caminho do arquivo de ajuda.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o caminho do arquivo de ajuda e a ID de contexto do tópico que explica o erro, se possível.  
  
> [!NOTE]
> Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)