---
title: Análise de código para código gerenciado
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e306d19dcf10e929bfb6432e6b6eb585996657f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550855"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visão geral da análise de código para código gerenciado no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos analisadores de [código](../code-quality/roslyn-analyzers-overview.md)baseados em .net Compiler Platform. Este tópico aborda a análise herdada. Para saber mais sobre a análise de código baseada em .NET Compiler Platform, confira [visão geral dos analisadores baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

A análise de código para código gerenciado analisa os assemblies gerenciados e as informações de relatórios sobre os assemblies, como violações das regras de programação e design estabelecidas nas [diretrizes de design do .net](/dotnet/standard/design-guidelines/).

A ferramenta de análise representa as verificações que executa durante uma análise como mensagens de aviso. As mensagens de aviso identificam problemas de programação e de design relevantes e, quando possível, fornecem informações de como corrigir o problema.

> [!NOTE]
> A análise herdada (análise de código estático) não tem suporte para projetos .NET Core e .NET Standard no Visual Studio. Se você executar a análise de código em um projeto do .NET Core ou .net Standard como parte do MSBuild, você verá um erro **semelhante a erro: CA0055 : Não foi possível identificar a \<plataforma para o >** . dll. Para analisar o código em projetos .NET Core ou .NET Standard, use analisadores de [código](../code-quality/roslyn-analyzers-overview.md) em vez disso.

## <a name="ide-integrated-development-environment-integration"></a>Integração do IDE (ambiente de desenvolvimento integrado)

Você pode executar a análise de código em seu projeto manualmente ou automaticamente.

Para executar a análise de código cada vez que você criar um projeto, selecione **Habilitar análise de código no Build** na página de propriedades do projeto. Para obter mais informações, confira [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para executar a análise de código manualmente em um projeto, na barra de menus, escolha **analisar** > **executar análise** > de código**executar análise de código no \<projeto >** .

## <a name="rule-sets"></a>Conjuntos de regras

As regras de análise de código gerenciado são agrupadas em [conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Você pode usar um dos conjuntos de regras padrão da Microsoft ou pode [criar um conjunto de regras personalizadas](../code-quality/how-to-create-a-custom-rule-set.md) para atender a uma necessidade específica.

## <a name="suppress-warnings"></a>Suprimir avisos

Geralmente, é útil indicar que um aviso não é aplicável. Isso informa ao desenvolvedor e a outras pessoas que poderão examinar o código mais tarde, que um aviso foi investigado e, em seguida, suprimido ou ignorado.

A supressão na origem de avisos é implementada por meio de atributos personalizados. Para suprimir um aviso, adicione o atributo `SuppressMessage` ao código-fonte, conforme é mostrado no exemplo a seguir:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Para obter mais informações, consulte [suprimir avisos](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Se você migrar um projeto para o Visual Studio 2017 ou o Visual Studio 2019, você poderá, de repente, enfrentar um grande número de avisos de análise de código. Se você não estiver pronto para corrigir os avisos e quiser se tornar produtivo imediatamente, você poderá fazer a *linha de base* do estado de análise do seu projeto. No menu **analisar** , selecione **executar análise de código e suprimir problemas ativos**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in

Em uma organização, talvez convenha exigir que todos os check-ins satisfaçam determinadas políticas. Especificamente, convém garantir que estas políticas sejam seguidas:

- Não há erros de compilação no código que está sendo verificado.

- A análise de código é executada como parte da compilação mais recente.

Você pode garantir isso especificando políticas de check-in. Para obter mais informações, consulte aprimorando a [qualidade do código com as políticas de check-in do projeto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integração do Team Build

Você pode usar os recursos integrados do sistema de build para executar a ferramenta de análise como parte do processo de build. Para obter mais informações, confira [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Consulte também

- [Visão geral de analisadores baseados em .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
