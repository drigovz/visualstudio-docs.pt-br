---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b0739294f5c2b003baa7e221c7e617456fda89e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822036"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Esse método retorna um serviço solicitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `vendor`  
 [in] `GUID` de um fornecedor (um valor nulo é aceitável).  
  
 `language`  
 [in] `GUID` de uma linguagem (um valor nulo é aceitável).  
  
 `iid`  
 [in] `IID` do serviço a obter.  
  
 `ppService`  
 [out] Uma interface para o serviço solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Passe o `IID` para o [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interface (`IID_IEEVisualizerServiceProvider`) para ver se o serviço Visualizador de tipo está disponível. Se assim, o avaliador de expressão pode obter o [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interface para oferecer suporte a visualizadores de tipo. Ver [visualização e exibindo os dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualizar e exibir dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)