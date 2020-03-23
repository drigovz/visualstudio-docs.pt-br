---
title: Configurar análise de código
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
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431346"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Como: Configurar a análise de legado para código gerenciado

No Visual Studio, você pode escolher entre uma lista de [conjuntos](../code-quality/rule-set-reference.md) de regras de análise de código para aplicar a um projeto de código gerenciado. Por padrão, o conjunto de **regras recomendadas da Microsoft** é selecionado, mas você pode aplicar um conjunto de regras diferente, se desejar. Os conjuntos de regras podem ser aplicados a um ou vários projetos em uma solução.

> [!NOTE]
> Este artigo se aplica à análise de legado e não a [analisadores de código baseados em plataforma .NET Compiler](use-roslyn-analyzers.md). .

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configure um conjunto de regras para um projeto .NET Framework

1. Abra a guia Análise de **Código** nas páginas de propriedade do projeto. É possível fazer isso de qualquer uma destas maneiras:

   - No **Solution Explorer,** selecione o projeto. Na barra de menu, **selecione Analisar** > **configurar análise de** > código**para>\<nome do projeto **.

   - Clique com o botão direito do mouse no projeto no **Solution Explorer** e selecione **Propriedades**e selecione a guia Análise **de código.**

2. Nas listas **Configuração** e **Plataforma,** selecione a configuração de compilação e a plataforma de destino.

::: moniker range="vs-2017"

3. Para executar a análise de código toda vez que o projeto for construído usando a configuração selecionada, **selecione Ativar análise de código na compilação**. Você também pode executar a análise de código manualmente selecionando **Analyze** > **Run Code Analysis** > **Analysis no \<projectname>**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Para executar a análise de código toda vez que o projeto for construído usando a configuração selecionada, **selecione Executar na compilação** na seção **analisadores binários.** Você também pode executar a análise de código legado manualmente, veja [Como: Executar análise de código legado manualmente para código gerenciado](how-to-run-legacy-code-analysis-manually-for-managed-code.md) para obter mais detalhes.

::: moniker-end

4. Para visualizar os avisos do código gerado, limpe os **resultados de Supressão da** caixa de seleção de código gerada.

    > [!NOTE]
    > Esta opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode visualizar e manter o código fonte de um formulário ou um modelo, e ele não será substituído.

::: moniker range="vs-2017"

5. No **Executar este set list de regras,** faça um dos seguintes:

::: moniker-end

::: moniker range=">=vs-2019"

5. Na lista **de regras ativas,** faça um dos seguintes:

::: moniker-end

   - Selecione o conjunto de regras que deseja usar.

   - Selecione Procurar ** \<>** para encontrar um conjunto de regras personalizado existente que não esteja na lista.

   - Defina um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar conjuntos de regras para vários projetos em uma solução

Por padrão, todos os projetos gerenciados de uma solução são atribuídos ao conjunto de regras de código *de regras recomendadas* da Microsoft. Você pode alterar os conjuntos de regras atribuídos aos projetos de uma solução na caixa de diálogo **Propriedades** para a solução.

1. Abra a solução no Visual Studio.

2. No menu **Analisar,** **selecione Configurar análise de código para solução**.

3. Se necessário, **expanda propriedades comuns**e selecione **Configurações de análise de código**.

4. Você pode especificar uma regra definida para um ou mais projetos:

    - Para especificar uma regra definida para um projeto individual, selecione o nome do projeto.

    - Para especificar um conjunto de regras para vários projetos, mantenha-se **em Ctrl** e selecione os nomes do projeto.

    - Para especificar todos os projetos **Shift** da solução, mantenha-se deslocado e clique na lista de projetos.

5. Selecione o campo **Definir** regras de um projeto e, em seguida, selecione o nome do conjunto de regras que deseja aplicar.

## <a name="see-also"></a>Confira também

- [Referência do conjunto de regras da análise de código](../code-quality/rule-set-reference.md)
