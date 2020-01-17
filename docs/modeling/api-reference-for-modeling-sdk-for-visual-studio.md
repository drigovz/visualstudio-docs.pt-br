---
title: Referência da API do SDK de modelagem
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4be65a94892aa87dbc7f146ce3671336a37558
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113740"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referência de API do SDK de Modelagem para Visual Studio

O SDK de modelagem e visualização do Visual Studio fornece a plataforma na qual suas ferramentas de linguagens específicas de domínio (DSL) são criadas.

Esta seção contém o material de referência para os namespaces que têm nomes que começam com "Microsoft.VisualStudio.Modeling".

|Namespace|Conteúdo|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes como ModelElement, que é a classe base de todas as classes de domínio que você define em uma DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes que fazem parte de uma definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Os modelo Store visualizador e o desempenho ferramentas de medição.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes como ShapeElement, que é a classe base de todas as formas que você define em uma DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de seleção e de gesto.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|A API do designer de definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internas do designer de definição de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permitem que você estenda o designer DSL com comandos, gestos e validação.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensão para ModelElement que implementam a extensibilidade de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidade|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite que você torne partes de um modelo somente leitura.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|A API do Modelbus, o que ajuda você a integrar modelos diferentes.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|A caixa de diálogo que permite aos usuários navegar a modelos e elementos para criar referências do Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|O serviço do seletor.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Estrutura de adaptador do Modelbus para Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|A caixa de diálogo de seletor que permite aos usuários navegar a modelos e elementos para criar referências do Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|A interface entre DSLs e o Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite definir comandos de menu de atalho (contexto).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite que você defina restrições de validação.|

## <a name="see-also"></a>Veja também

- [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)
