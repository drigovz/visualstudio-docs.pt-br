---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786256"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Estabelece uma conexão entre o objeto de ponto de conexão simples e o coletor do cliente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdisp`  
 [in] Ponteiro para o `IDispatch` interface no cliente do coletor de aviso. O coletor do cliente recebe chamadas de saída do ponto de conexão simples.  
  
 `pdwCookie`  
 [out] Ponteiro para um token retornado que identifica exclusivamente essa conexão. O chamador usa esse token posteriormente para excluir a conexão, passando-o para o `ISimpleConnectionPoint::Unadvise` método. Se a conexão não foi estabelecida com êxito, esse valor é zero.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método estabelece uma conexão entre o objeto de ponto de conexão simples e o coletor do cliente.  
  
## <a name="see-also"></a>Consulte também  
 [ISimpleConnectionPoint Interface](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)