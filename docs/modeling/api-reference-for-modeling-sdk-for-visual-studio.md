---
title: Referência de API para o SDK de modelagem
description: Saiba como o Visual Studio Visualization and Modeling SDK fornece a plataforma na qual suas ferramentas de DSLs (linguagens específicas de domínio) são criadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b9393c8e01cb304b6a89ac9b400f3efc29d8c056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861901"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referência de API do SDK de Modelagem para Visual Studio

O SDK de visualização e modelagem do Visual Studio fornece a plataforma na qual suas ferramentas de DSL (linguagens específicas de domínio) são criadas.

Esta seção contém material de referência para namespaces que têm nomes que começam com "Microsoft. VisualStudio. Modeling".

|Namespace|Conteúdo|
|-|-|
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
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Estrutura do adaptador ModelBus para Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|A caixa de diálogo seletor que permite aos usuários navegar para modelos e elementos para criar referências de ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|A interface entre DSLs e o Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite que você defina comandos de menu de atalho (contexto).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite definir restrições de validação.|

## <a name="see-also"></a>Confira também

- [Personalizando transformação de texto T4](../modeling/customizing-t4-text-transformation.md)
