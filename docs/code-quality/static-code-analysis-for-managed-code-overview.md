---
title: Análise herdada para código gerenciado
ms.date: 06/12/2019
description: Saiba mais sobre a análise herdada no Visual Studio. Veja como suprimir avisos e como executar análises manualmente, automaticamente e durante os check-ins e compilações.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e8d9ddf88086772e0cd21bde856184954bc7143b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867679"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Visão geral da análise herdada para código gerenciado no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos [analisadores de código](../code-quality/roslyn-analyzers-overview.md)baseados em .net Compiler Platform. Este tópico aborda a análise herdada. Para saber mais sobre a análise de código baseada em .NET Compiler Platform, confira [visão geral dos analisadores baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

A análise de código para código gerenciado analisa os assemblies gerenciados e as informações de relatórios sobre os assemblies, como violações das regras de programação e design estabelecidas nas [diretrizes de design do .net](/dotnet/standard/design-guidelines/).

A ferramenta de análise representa as verificações que executa durante uma análise como mensagens de aviso. As mensagens de aviso identificam problemas de programação e de design relevantes e, quando possível, fornecem informações de como corrigir o problema.

> [!NOTE]
> A análise herdada (análise de código estático) não tem suporte para projetos .NET Core e .NET Standard no Visual Studio. Se você executar a análise de código em um projeto do .NET Core ou .NET Standard como parte do MSBuild, verá um erro semelhante a **erro: CA0055: não foi possível identificar \<your.dll> a plataforma para**. Para analisar o código em projetos .NET Core ou .NET Standard, use [analisadores de código](../code-quality/roslyn-analyzers-overview.md) em vez disso.

## <a name="ide-integrated-development-environment-integration"></a>Integração do IDE (ambiente de desenvolvimento integrado)

Você pode executar a análise de código em seu projeto manualmente ou automaticamente.

Para executar a análise de código cada vez que você criar um projeto, selecione a opção na página de propriedades de **análise de código** do projeto. Para obter mais informações, consulte [como habilitar e desabilitar a análise automática de código](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para executar a análise de código manualmente em um projeto, na barra de menus, escolha **analisar**  >  **executar análise**  >  **de código \<project> executar análise de código em**.

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

::: moniker range="vs-2017"

> [!NOTE]
> Se você migrar um projeto para o Visual Studio 2017, poderá, de repente, enfrentar um grande número de avisos de análise de código. Se você não estiver pronto para corrigir os avisos, poderá suprimir todos eles escolhendo **analisar**  >  **executar análise de código e suprimir problemas ativos**.
>
> ![Executar análise de código e suprimir problemas no Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Se você migrar um projeto para o Visual Studio 2019, poderá, de repente, enfrentar um grande número de avisos de análise de código. Se você não estiver pronto para corrigir os avisos, poderá suprimir todos eles escolhendo **analisar**  >  **Compilar e suprimir problemas ativos**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in

Em uma organização, talvez convenha exigir que todos os check-ins satisfaçam determinadas políticas. Especificamente, convém garantir que estas políticas sejam seguidas:

- Não há erros de compilação no código que está sendo verificado.

- A análise de código é executada como parte da compilação mais recente.

Você pode garantir isso especificando políticas de check-in. Para obter mais informações, consulte [aprimorando a qualidade do código com as políticas de check-in do projeto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integração do Team Build

Você pode usar os recursos integrados do sistema de build para executar a ferramenta de análise como parte do processo de build. Para obter mais informações, confira [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Confira também

- [Visão geral de analisadores baseados em .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Como habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
