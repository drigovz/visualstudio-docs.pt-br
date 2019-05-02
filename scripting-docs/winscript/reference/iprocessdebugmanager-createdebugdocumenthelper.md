---
title: IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38de1e828ccd1715fb83cc76c06ba837818d2af0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002351"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Cria um novo auxiliar de documento de depuração para este aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `punkOuter`  
 [in] Se o objeto retornado deve ser agregada, `punkOuter` é um ponteiro de interface para o controle `IUnknown`. Caso contrário, ele é um ponteiro nulo.  
  
 `pddh`  
 [out] O objeto documento auxiliar de depuração para este aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um novo auxiliar de documento de depuração para este aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)