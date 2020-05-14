---
title: Visualização e Visualização de Dados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712372"
---
# <a name="visualizing-and-viewing-data"></a>Visualização e visualização de dados
Visualizadores de digitação e espectadores personalizados apresentam dados de uma maneira que é rapidamente significativa para um desenvolvedor. O avaliador de expressão (EE) pode suportar visualizadores de tipos de terceiros, bem como fornecer seus próprios espectadores personalizados.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina quantos visualizadores de tipo e espectadores personalizados estão associados ao tipo do objeto, chamando o método [GetCustomViewerCount.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Se houver pelo menos um visualizador de tipo ou visualizador personalizado disponível, o Visual Studio chama o método [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para recuperar uma lista desses visualizadores e espectadores (na verdade, uma lista de s que implementa os visualizadores e espectadores) e os apresenta ao usuário.

## <a name="supporting-type-visualizers"></a>Visualizadores de tipo de suporte
 Há uma série de interfaces que o EE deve implementar para suportar visualizadores de tipo. Essas interfaces podem ser divididas em duas grandes categorias: interfaces que listam os visualizadores de tipo e interfaces que acessam os dados de propriedade.

### <a name="listing-type-visualizers"></a>Visualizadores de tipo de listagem
 O EE suporta listar os visualizadores do `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList`tipo na sua implementação e . Esses métodos passam a chamada para os métodos correspondentes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 O [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) é obtido chamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Este método requer a interface [IDebugBinder3,](../../extensibility/debugger/reference/idebugbinder3.md) que é obtida a partir da interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passada para [AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`também requer as interfaces [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) que foram passadas para `IDebugParsedExpression::EvaluateSync`. A interface final necessária `IEEVisualizerService` para criar a interface é a interface [IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) que o EE implementa. Esta interface permite que sejam feitas alterações na propriedade que está sendo visualizada. Todos os dados de propriedade são encapsulados em uma interface [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) que também é implementada pelo EE.

### <a name="accessing-property-data"></a>Acessando dados de propriedade
 O acesso aos dados da propriedade é feito através da interface [IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Para obter essa interface, o Visual Studio chama [o QueryInterface](/cpp/atl/queryinterface) no objeto da propriedade para obter a interface [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementada no mesmo `IPropertyProxyEESide` objeto que implementa a interface [IDebugProperty3)](../../extensibility/debugger/reference/idebugproperty3.md) e, em seguida, chama o método [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter a interface.

 Todos os dados passados `IPropertyProxyEESide` para dentro e para fora da interface são encapsulados na interface [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Esta interface representa uma matriz de bytes e é implementada tanto pelo Visual Studio quanto pelo EE. Quando os dados de uma propriedade devem ser `IEEDataStorage` alterados, o Visual Studio cria um objeto que mantém os novos dados e chama [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) com esse objeto de dados, a fim de obter um novo `IEEDataStorage` objeto que, por sua vez, é passado para o [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para atualizar os dados da propriedade. `IPropertyProxyEESide::CreateReplacementObject`permite ao EE instanciar sua `IEEDataStorage` própria classe que implementa a interface.

## <a name="supporting-custom-viewers"></a>Suporte a espectadores personalizados
 O `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` sinalizador é `dwAttrib` definido no campo da estrutura [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (retornado por uma chamada para [getPropertyInfo)](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)para indicar que o objeto tem um visualizador personalizado associado a ele. Quando este sinalizador é definido, o Visual Studio obtém a interface [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) da interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) usando [QueryInterface](/cpp/atl/queryinterface).

 Se o usuário selecionar um visualizador personalizado, o Visual Studio `CLSID` instanciar o visualizador personalizado usando o visualizador fornecido pelo `IDebugProperty3::GetCustomViewerList` método. O Visual Studio então chama [o DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar o valor ao usuário.

 Normalmente, `IDebugCustomViewer::DisplayValue` apresenta uma visão somente de leitura dos dados. Para permitir alterações nos dados, o EE deve implementar uma interface personalizada que suporte a alteração de dados em um objeto de propriedade. O `IDebugCustomViewer::DisplayValue` método usa essa interface personalizada para suportar a alteração dos dados. O método procura a interface `IDebugProperty2` personalizada na `pDebugProperty` interface passada como argumento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Suporte tanto visualizadores de tipo quanto espectadores personalizados
 Um EE pode suportar visualizadores de tipo e espectadores personalizados nos métodos [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Primeiro, o EE adiciona o número de espectadores personalizados que está fornecendo ao valor retornado pelo método [GetCustomViewerCount.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Em segundo lugar, o `CLSID`EE anexa o s de seus próprios espectadores personalizados à lista devolvida pelo método [GetCustomViewerList.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="see-also"></a>Confira também
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
- [Digite visualizador e visualizador personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
