---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa0ec16ce47e7e96b9ef19c9e46e5ec10ec55177
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863640"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Atualiza os dados do objeto com o objeto de dados fornecido e retorna um novo objeto de dados que representa os dados do objeto novo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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

