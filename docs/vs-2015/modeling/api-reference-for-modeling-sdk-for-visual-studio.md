---
title: Referência de API para o SDK de modelagem
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65f8703597d6297afde6e2685594784fdd1d755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672838"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referência de API do SDK de Modelagem para Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O SDK de visualização e modelagem do Visual Studio fornece a plataforma na qual as ferramentas de DSL (linguagens específicas de domínio) e UML são criadas.

> [!NOTE]
> Para obter informações sobre a API de modelagem UML, consulte [referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Para obter informações sobre a transformação de texto, consulte [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md).

 Esta seção contém material de referência para namespaces que têm nomes que começam com "Microsoft. VisualStudio. Modeling".

|Namespace|Conteúdo|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes como ModelElement, que é a classe base de todas as classes de domínio que você define em uma DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes que fazem parte de uma definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|O Visualizador do repositório de modelos e as ferramentas de medição de desempenho.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes como ShapeElement, que é a classe base de todas as formas que você define em uma DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de gesto e seleção.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|A API do designer de definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internas do designer de definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permitem estender o designer de DSL com comandos, gestos e validação.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensão para ModelElement que implementam a extensibilidade de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidade|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite que você torne partes de um modelo somente leitura.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|A API ModelBus, que ajuda você a integrar modelos diferentes.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|A caixa de diálogo que permite aos usuários navegar para modelos e elementos para criar referências de ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|O serviço de seletor.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Estrutura de adaptador ModelBus para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|A caixa de diálogo seletor que permite aos usuários navegar para modelos e elementos para criar referências de ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|A interface entre DSLs e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite que você defina comandos de menu de atalho (contexto).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite definir restrições de validação.|

## <a name="see-also"></a>Confira também

- [Referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Personalizando transformação de texto T4](../modeling/customizing-t4-text-transformation.md)
