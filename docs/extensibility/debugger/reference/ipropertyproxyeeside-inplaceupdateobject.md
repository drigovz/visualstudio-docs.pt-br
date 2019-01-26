---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15e2e3382484040be4117b355fb93f48788c7b18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952984"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Atualiza os dados do objeto com o objeto de dados fornecido e retorna um novo objeto de dados que representa os dados do objeto novo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataIn`  
 [in] Uma [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contém os novos dados.  
  
 `dataOut`  
 [out] Retorna um novo `IEEDataStorage` objeto que contém os dados substituídos.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Na verdade, esse método atualiza os dados do objeto. Os dados em retornado [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto não precisa ser o mesmo que os dados de entrada `IEEDataStorage` objeto, mas o objeto retornado deve refletir o valor da propriedade atual.  
  
 O objeto de dados de entrada não costuma ser implementado pelo EE. No entanto, o objeto retornado por esse método sempre é implementado pelo EE, que permite que o implemente EE o `IEEDataStorage` interface em qualquer classe for desejada.  
  
 O [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) método cria um objeto de dados com base no objeto de entrada de dados, mas não afeta os dados de original da propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)