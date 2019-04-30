---
title: IDispError::GetHelpInfo | Microsoft Docs
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
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446914"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Retorna o caminho do arquivo de Ajuda e a ID do contexto do tópico que explica o erro, se possível.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrFileName`  
 [out] Cadeia de caracteres que contém o caminho totalmente qualificado do arquivo de Ajuda. Se não há nenhum arquivo de Ajuda ou ocorre um erro, o valor retornado é NULL.  
  
 `pdwContext`  
 [out] A ID do contexto de ajuda para o erro. Se não houver nenhum arquivo de Ajuda (se `pbstrFileName` é NULL), esse parâmetro não tem nenhum significado.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Ocorreu um erro específico do provedor.|  
|`E_INVALIDARG`|`pbstrFileName` ou `pdwContext` era nulo.|  
|`E_OUTOFMEMORY`|O provedor não pôde alocar memória suficiente no qual retornar o caminho do arquivo de Ajuda.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o caminho do arquivo de Ajuda e a ID do contexto do tópico que explica o erro, se possível.  
  
> [!NOTE]
> Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)