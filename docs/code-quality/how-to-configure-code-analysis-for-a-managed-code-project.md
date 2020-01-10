---
title: Configurar a análise de código
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587557"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Como: configurar a análise herdada para código gerenciado

No Visual Studio, você pode escolher em uma lista de conjuntos de [regras](../code-quality/rule-set-reference.md) de análise de código para aplicar a um projeto de código gerenciado. Por padrão, o **Microsoft mínimo recomendado regras** conjunto de regras é selecionado, mas você pode aplicar uma regra diferente, defina se desejado. Conjuntos de regras podem ser aplicados a um ou vários projetos em uma solução.

> [!NOTE]
> Este artigo se aplica à análise herdada e não a [analisadores de código baseados em .net Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurar um conjunto de regras para um projeto .NET Framework

1. Abra o **análise de código** guia nas páginas de propriedades do projeto. É possível fazer isso de qualquer uma destas maneiras:

   - Na **Gerenciador de soluções**, selecione o projeto. Na barra de menus, selecione **Analyze** > **configurar a análise de código** > **para \<projectname >** .

   - Clique com botão direito no projeto no **Gerenciador de soluções** e selecione **Properties**e, em seguida, selecione o **análise de código** guia.

2. No **Configuration** e **plataforma** listas, selecione a plataforma de destino e a configuração de compilação.

::: moniker range="vs-2017"

3. Para executar a análise de código toda vez que o projeto for criado usando a configuração selecionada, selecione **Habilitar análise de código na compilação**. Você também pode executar a análise de código manualmente selecionando **Analyze** > **executar análise de código** > **executar análise de código em \<projectname >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Para executar a análise de código toda vez que o projeto é compilado usando a configuração selecionada, selecione **executar na compilação** na seção **analisadores binários** . Você também pode executar a análise de código manualmente selecionando **Analyze** > **executar análise de código** > **executar análise de código em \<projectname >** .

::: moniker-end

4. Para exibir avisos do código gerado, desmarque a **Suprimir resultados do código gerado** caixa de seleção.

    > [!NOTE]
    > Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte de um formulário ou modelo e ele não será substituído.

::: moniker range="vs-2017"

5. No **executar este conjunto de regras** lista, siga um destes procedimentos:

::: moniker-end

::: moniker range=">=vs-2019"

5. Na lista **regras ativas** , siga um destes procedimentos:

::: moniker-end

   - Selecione o conjunto de regras que você deseja usar.

   - Selecione **\<procurar >** para localizar um conjunto de regras personalizadas existente que não esteja na lista.

   - Definir um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar conjuntos de regras para vários projetos em uma solução

Por padrão, todos os projetos gerenciados de uma solução são atribuídos a *Microsoft mínimo recomendado regras* conjunto de regras de análise de código. Você pode alterar os conjuntos de regras que são atribuídos aos projetos de uma solução com o **propriedades** caixa de diálogo para a solução.

1. Abra a solução no Visual Studio.

2. Sobre o **Analyze** menu, selecione **configurar a análise de código para solução**.

3. Se necessário, expanda **propriedades comuns**e, em seguida, selecione **configurações de análise de código**.

4. Você pode especificar uma regra definida para um ou mais projetos:

    - Para especificar uma regra definida para um projeto individual, selecione o nome do projeto.

    - Para especificar uma regra definida para vários projetos, mantenha pressionada **Ctrl** e selecione os nomes de projeto.

    - Para especificar todos os projetos na solução, mantenha pressionada **Shift** e clique na lista de projetos.

5. Selecione o **do conjunto de regras** campo de um projeto e, em seguida, selecione o nome da regra definida que você deseja aplicar.

## <a name="see-also"></a>Veja também

- [Referência do conjunto de regras de análise de código](../code-quality/rule-set-reference.md)
