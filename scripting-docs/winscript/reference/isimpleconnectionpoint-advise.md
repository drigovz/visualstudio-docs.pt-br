---
title: 'ISimpleConnectionPoint:: Advise | Microsoft Docs'
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
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571830"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Estabelece uma conexão entre o objeto do ponto de conexão simples e o coletor do cliente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdisp`  
 no Ponteiro para a interface de `IDispatch` no coletor de aviso do cliente. O coletor do cliente recebe chamadas de saída do ponto de conexão simples.  
  
 `pdwCookie`  
 fora Ponteiro para um token retornado que identifica exclusivamente essa conexão. O chamador usará esse token posteriormente para excluir a conexão, passando-a para o método `ISimpleConnectionPoint::Unadvise`. Se a conexão não tiver sido estabelecida com êxito, esse valor será zero.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método estabelece uma conexão entre o objeto do ponto de conexão simples e o coletor do cliente.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)  
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)