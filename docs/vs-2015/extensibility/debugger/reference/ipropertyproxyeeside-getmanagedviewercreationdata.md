---
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5161894875ac683e5a6e49ae623bd6025531006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199524"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera informações sobre o visualizador para esse tipo de propriedade para criar uma instância desse visualizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `assemName`  
 fora Retorna o nome do assembly que contém este objeto.  
  
 `assemBytes`  
 fora Retorna um objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contém os bytes de assembly deste objeto (esse é um valor nulo se nenhum byte estiver disponível).  
  
 `assemPdb`  
 fora Retorna um `IEEDataStorage` objeto que contém as informações de repositório de símbolo para esse objeto (esse é um valor nulo se nenhum armazenamento de símbolo está disponível).  
  
 `className`  
 fora Retorna o nome da classe que contém este objeto.  
  
 `alr`  
 fora Retorna um valor da enumeração [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) que indica o local do assembly.  
  
 `replacementOk`  
 fora Retorna zero ( `TRUE` ) se o valor desse objeto puder ser alterado; zero ( `FALSE` ) se o objeto for somente leitura.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado por visualizadores de tipo para criar uma instância de um visualizador gerenciado.  
  
## <a name="see-also"></a>Consulte Também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
