---
title: Programando com a API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0cd086221b1c0ee6a4e2111cda543a3f8f4ec0e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871759"
---
# <a name="programming-with-the-uml-api"></a>Programando com a API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A API UML do Visual Studio permite que você escreva código para criar, ler e atualizar modelos e diagramas UML. Para ver quais versões do Visual Studio oferecem suporte a modelos UML, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Além das páginas de referência da API, os tópicos a seguir descrevem a API.

|Tópico|Tipos de exemplo e métodos descritos|Recursos descritos|
|-----------|-----------------------------------------|------------------------|
|[Navegar em relações com a API UML](../modeling/navigate-relationships-with-the-uml-api.md)|Elementos UML e suas propriedades e associações. Por exemplo, ielemento e seus descendentes, incluindo: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|No Visual Studio, os modelos UML estão em conformidade com a versão de especificação UML 2.1.2, que pode ser obtida na [página de recursos UML](http://go.microsoft.com/fwlink/?LinkId=160796). Cada tipo é uma interface que tem o mesmo nome que o tipo UML, prefixado com "I".|
|[Criar elementos e relações em modelos UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Cada tipo de elemento tem métodos para criar seus filhos.|
|[Exibir um modelo UML em diagramas](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Cada elemento em um modelo pode ser representado como uma forma em um diagrama. Em alguns casos, você pode criar novas formas para cada objeto. Você pode mover, redimensionar, colorir e recolher ou expandir essas formas.|
|[Navegar no modelo UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|O repositório de modelos armazena o modelo.<br /><br /> O contexto do diagrama fornece acesso ao diagrama e ao repositório atuais.|
|[Vincular atualizações de modelo UML usando transações](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Você pode vincular uma série de alterações em uma transação.|
|[Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Você pode estender a funcionalidade de um diagrama definindo comandos invocados clicando duas vezes e arrastando para o diagrama.|
|[Definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Você pode definir regras de validação que ajudam a garantir que um modelo esteja de acordo com as restrições especificadas.|
|[Obter elementos de modelo UML de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|Ielemento, IShape|Quando um elemento é arrastado do Gerenciador de modelos UML ou de um diagrama UML para outro diagrama ou aplicativo, ele é serializado como um IDataObject.|
|[Editar diagramas de sequência UML usando a API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Criar e atualizar um diagrama de interação é ligeiramente diferente de trabalhar com os outros tipos de diagramas.|
|[Estender diagramas de camada](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Você pode escrever código para criar e editar diagramas de camada e também validar o código do programa em relação a eles.|

## <a name="about-the-implementation"></a>Sobre a implementação
 As ferramentas de modelagem UML são criadas [!INCLUDE[dsl](../includes/dsl-md.md)]no. Cada pacote e cada diagrama é representado por um [!INCLUDE[dsl](../includes/dsl-md.md)] modelo, e uma coleção de regras e outros métodos mantém a consistência entre eles.

 Tipos dessa plataforma são visíveis em alguns dos assemblies que você referencia para gravar extensões UML. Embora seja possível fazer extensões para as ferramentas UML acessando [!INCLUDE[dsl](../includes/dsl-md.md)] a API, você deve ter em mente as seguintes considerações:

- Você pode achar que algumas alterações aparentemente simples apresentam inconsistências e efeitos inesperados.

- A implementação pode mudar no futuro, para que as adaptações feitas usando a [!INCLUDE[dsl](../includes/dsl-md.md)] API possam não funcionar mais.

## <a name="the-api-assemblies"></a>Os assemblies de API
 Esta tabela resume os assemblies que fornecem extensibilidade para as ferramentas UML e os namespaces que você recomenda usar.

|Assembly|Namespaces|Fornece acesso a:|
|--------------|----------------|-------------------------|
|Microsoft.VisualStudio.Uml.Interfaces|Os|Os tipos UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Microsoft. VisualStudio. ArchitectureTools. Extensibility. Uml|[Métodos de criação](../modeling/create-elements-and-relationships-in-uml-models.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation|[Diagramas e formas](../modeling/display-a-uml-model-on-diagrams.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility|[O projeto de modelagem](../modeling/read-a-uml-model-in-program-code.md)|
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Extensão de comando de menu](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Transações de desfazer vinculadas](../modeling/link-uml-model-updates-by-using-transactions.md).|
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Validação](../modeling/define-validation-constraints-for-uml-models.md)|
||(outros namespaces)|Recomendado apenas para uso avançado.|
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Manipuladores](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)de gestos.|
||(outros namespaces)|Recomendado apenas para uso avançado.|
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|[Links para itens de trabalho](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.WorkItemTracking.Client|Microsoft.TeamFoundation.WorkItemTracking.Client|[Itens de trabalho e seus campos](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.Client|Microsoft.TeamFoundation.Client|[Itens de trabalho e seus campos](../modeling/define-a-work-item-link-handler.md).|
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Exportar e importar para componentes do MEF](../modeling/define-and-install-a-modeling-extension.md)|
|System.Linq|<xref:System.Linq>|[Fácil manipulação de coleções, especialmente ao lidar com relações](../modeling/navigate-relationships-with-the-uml-api.md).|

## <a name="see-also"></a>Consulte também
 [Estender diagramas e modelos UML](../modeling/extend-uml-models-and-diagrams.md) [Referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
