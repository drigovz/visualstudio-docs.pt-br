---
title: Visualizando e exibindo dados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 719a2b3d073d90ff3977496c7f98ebecb1ab48a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696308"
---
# <a name="visualizing-and-viewing-data"></a>Visualizando e exibindo dados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizeres de tipo e visualizadores personalizados apresentam dados de uma maneira que é rapidamente significativa para um desenvolvedor. O avaliador de expressão (EE) pode dar suporte a visualizadores de tipo de terceiros, bem como fornecer seus próprios visualizadores personalizados.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Determina quantos visualizadores de tipo e visualizadores personalizados estão associados ao tipo do objeto chamando o método [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Se houver pelo menos um visualisador ou visualizador personalizado disponível, o Visual Studio chamará o método [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para recuperar uma lista desses visualizadores e visualizadores (na verdade, uma lista de `CLSID` s que implementam os visualizadores e espectadores) e os apresentará ao usuário.  
  
## <a name="supporting-type-visualizers"></a>Visualizadores de tipo de suporte  
 Há várias interfaces que o EE deve implementar para dar suporte a visualizadores de tipos. Essas interfaces podem ser divididas em duas categorias amplas: as que listam os visualizadores de tipo e os que acessam os dados de propriedade.  
  
### <a name="listing-type-visualizers"></a>Listando visualizadores de tipo  
 O EE dá suporte à listagem dos visualizadores de tipo em sua implementação de `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList` . Esses métodos passam a chamada para os métodos correspondentes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 O [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) é obtido chamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Esse método requer a interface [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , que é obtida da interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passada para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` também requer as interfaces [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) que foram passadas para `IDebugParsedExpression::EvaluateSync` . A interface final necessária para criar a `IEEVisualizerService` interface é a interface [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , que o EE implementa. Essa interface permite que as alterações sejam feitas na propriedade que está sendo visualizada. Todos os dados de propriedade são encapsulados em uma interface [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , que também é implementada pelo EE.  
  
### <a name="accessing-property-data"></a>Acessando dados de propriedade  
 O acesso aos dados da propriedade é feito por meio da interface [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Para obter essa interface, o Visual Studio chama [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) no objeto de propriedade para obter a interface [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementada no mesmo objeto que implementa a interface [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ) e, em seguida, chama o método [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter a `IPropertyProxyEESide` interface.  
  
 Todos os dados passados para dentro e fora da `IPropertyProxyEESide` interface são encapsulados na interface [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) . Essa interface representa uma matriz de bytes e é implementada pelo Visual Studio e pelo EE. Quando os dados de uma propriedade são alterados, o Visual Studio cria um `IEEDataStorage` objeto que contém os novos dados e chama [ReplaceObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) com esse objeto de dados para obter um novo `IEEDataStorage` objeto que, por sua vez, é passado para [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para atualizar os dados da propriedade. `IPropertyProxyEESide::CreateReplacementObject` permite que o EE instancie sua própria classe que implementa a `IEEDataStorage` interface.  
  
## <a name="supporting-custom-viewers"></a>Suporte a visualizadores personalizados  
 O sinalizador `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` é definido no `dwAttrib` campo da estrutura de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (retornada por uma chamada para [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) para indicar que o objeto tem um visualizador personalizado associado a ele. Quando esse sinalizador é definido, o Visual Studio obtém a interface [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) da interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) usando [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
 Se o usuário selecionar um visualizador personalizado, o Visual Studio criará uma instância do visualizador personalizado usando o visualizador `CLSID` fornecido pelo `IDebugProperty3::GetCustomViewerList` método. Em seguida, o Visual Studio chama [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar o valor ao usuário.  
  
 Normalmente, `IDebugCustomViewer::DisplayValue` apresenta uma exibição somente leitura dos dados. Para permitir alterações nos dados, o EE deve implementar uma interface personalizada que ofereça suporte à alteração de dados em um objeto de propriedade. O `IDebugCustomViewer::DisplayValue` método usa essa interface personalizada para dar suporte à alteração dos dados. O método procura a interface personalizada na `IDebugProperty2` interface passada como o `pDebugProperty` argumento.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Dando suporte aos visualizadores de tipo e aos espectadores personalizados  
 Um EE pode dar suporte a visualizadores de tipo e visualizadores personalizados nos métodos [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . Primeiro, o EE adiciona o número de visualizadores personalizados que ele está fornecendo ao valor retornado pelo método [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Em segundo lugar, o EE acrescenta os `CLSID` s de seus próprios visualizadores personalizados à lista retornada pelo método [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizador de Tipo e Visualizador Personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
