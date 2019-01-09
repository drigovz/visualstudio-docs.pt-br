---
title: 'Idebugdocumenthost:: Oncreatedocumentcontext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0f8ce73e05fa8dd163564184361254fd58163ee
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096324"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Notifica o host que um novo contexto de documento está sendo criado e permite que o host, opcionalmente, retornar um controle desconhecido para o novo contexto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppunkOuter`  
 [out] Um objeto que controla o novo contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O host não fornece um objeto de controle.|  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que o host adicionar uma nova funcionalidade para os contextos de documento fornecido pelo auxiliar. Esse método pode retornar **E_NOTIMPL** ou um objeto externo nulo, nesse caso o chamador é responsável por criar o contexto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHost Interface](../../winscript/reference/idebugdocumenthost-interface.md)