---
title: Referência da API do SDK de modelagem
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a290227b120958b5bb3407393dcff33b247b20d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872016"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referência de API do SDK de Modelagem para Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O SDK de visualização e modelagem do Visual Studio fornece a plataforma na qual as ferramentas de DSL (linguagens específicas de domínio) e UML são criadas.

> [!NOTE]
> Para obter informações sobre a API de modelagem UML, consulte [referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Para obter informações sobre a transformação de texto, consulte Personalizando a [transformação de texto T4](../modeling/customizing-t4-text-transformation.md).

 Esta seção contém o material de referência para os namespaces que têm nomes que começam com "Microsoft.VisualStudio.Modeling".

|Namespace|Conteúdo|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes como ModelElement, que é a classe base de todas as classes de domínio que você define em uma DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes que fazem parte de uma definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Os modelo Store visualizador e o desempenho ferramentas de medição.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes como ShapeElement, que é a classe base de todas as formas que você define em uma DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de seleção e de gesto.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|A API do designer de definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internas do designer de definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permitem estender o designer de DSL com comandos, gestos e validação.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensão para ModelElement que implementam a extensibilidade de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidade|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite que você torne partes de um modelo somente leitura.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|A API do Modelbus, o que ajuda você a integrar modelos diferentes.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|A caixa de diálogo que permite aos usuários navegar a modelos e elementos para criar referências do Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|O serviço do seletor.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Estrutura de adaptador ModelBus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]para.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|A caixa de diálogo de seletor que permite aos usuários navegar a modelos e elementos para criar referências do Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|A interface entre DSLs e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite definir comandos de menu de atalho (contexto).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite que você defina restrições de validação.|

## <a name="see-also"></a>Consulte também

- [Referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)
