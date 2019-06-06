---
title: Análise estática de código para código gerenciado
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 81c4d6ba7cc4ae870c74733a4e78733c023e3f58
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713971"
---
# <a name="overview-of-static-code-analysis-for-managed-code-in-visual-studio"></a>Visão geral da análise de código estático para código gerenciado no Visual Studio

Visual Studio pode executar a análise de código gerenciado de duas maneiras: com *FxCop* análise estática de assemblies gerenciados e com os mais modernos *analisadores de Roslyn*. Este tópico aborda a análise de código estático do FxCop. Para saber mais sobre a análise de código usando analisadores de código, consulte [analisadores de visão geral do Roslyn](../code-quality/roslyn-analyzers-overview.md).

Análise de código para código gerenciado analisa os assemblies gerenciados e relata informações sobre assemblies, como violações das regras de programação e design definidas na [diretrizes de Design .NET](/dotnet/standard/design-guidelines/).

A ferramenta de análise representa as verificações que executa durante uma análise como mensagens de aviso. As mensagens de aviso identificam problemas de programação e de design relevantes e, quando possível, fornecem informações de como corrigir o problema.

> [!NOTE]
> Não há suporte para a análise de código estático para projetos do .NET Core e .NET Standard no Visual Studio. Se você executar a análise de código em um projeto .NET Core ou .NET Standard como parte do msbuild, você verá um erro semelhante ao **erro: CA0055 : Não foi possível identificar a plataforma para \<your.dll >** . Para analisar o código em projetos do .NET Core ou .NET Standard, use [analisadores de Roslyn](../code-quality/roslyn-analyzers-overview.md) em vez disso.

## <a name="ide-integrated-development-environment-integration"></a>Integração de IDE (ambiente de desenvolvimento integrado)

Você pode executar a análise de código em seu projeto automaticamente ou manualmente.

Para executar a análise de código sempre que você compila um projeto, selecione **habilitar a análise de código no Build** na página de propriedades do projeto. Para obter mais informações, confira [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para executar a análise de código manualmente em um projeto, na barra de menus, escolha **Analyze** > **executar análise de código** > **executar análise de código em \<projeto >** .

## <a name="rule-sets"></a>Conjuntos de regras

As regras de análise de código gerenciado são agrupadas em [conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Você pode usar um dos conjuntos de regra padrão Microsoft, ou você pode [criar um conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md) para atender a uma necessidade específica.

## <a name="suppress-warnings"></a>Suprimir avisos

Geralmente, é útil indicar que um aviso não é aplicável. Isso informa ao desenvolvedor e a outras pessoas que poderão examinar o código mais tarde, que um aviso foi investigado e, em seguida, suprimido ou ignorado.

Supressão de código-fonte de avisos é implementada por meio de atributos personalizados. Para suprimir um aviso, adicione o atributo `SuppressMessage` ao código-fonte, conforme é mostrado no exemplo a seguir:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Para obter mais informações, consulte [suprimir avisos](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Se você migrar um projeto para Visual Studio 2017 ou Visual Studio de 2019, você pode encontrar, de repente, com um grande número de avisos da análise de código. Se você não estiver pronto para corrigir os avisos e quer se tornar produtivo imediatamente, você poderá *linha de base* o estado de análise do seu projeto. Dos **Analyze** menu, selecione **executar análise de código e suprimir problemas ativos**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in

Em uma organização, talvez convenha exigir que todos os check-ins satisfaçam determinadas políticas. Especificamente, convém garantir que estas políticas sejam seguidas:

- Não há nenhum erro de compilação no check-in do código.

- Análise de código é executada como parte da compilação mais recente.

Você pode garantir isso especificando políticas de check-in. Para obter mais informações, consulte [aprimorando a qualidade do código com políticas de Check-in do projeto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integração do Team build

Você pode usar os recursos integrados do sistema de build para executar a ferramenta de análise como parte do processo de build. Para obter mais informações, confira [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
