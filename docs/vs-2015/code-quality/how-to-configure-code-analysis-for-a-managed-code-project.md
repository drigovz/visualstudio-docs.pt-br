---
title: 'Como: configurar a análise de código para um projeto de código gerenciado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658854"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Como configurar a análise de código para um projeto de código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] e [!INCLUDE[vsPro](../includes/vspro-md.md)] , você pode escolher em uma lista de conjuntos de *regras* de análise de código para aplicar a um projeto de código gerenciado. O conjunto de regras padrão é o mínimo de regras recomendadas da Microsoft. Você pode aplicar outro conjunto de regras a um projeto ou a todos os projetos em uma solução.

> [!NOTE]
> Para obter informações sobre como configurar um conjunto de regras para aplicativos Web ASP.NET, consulte [como: configurar a análise de código para um aplicativo web ASP.net](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Para configurar um conjunto de regras para um projeto .NET Framework

1. Em **Gerenciador de soluções**, clique no projeto.

2. No menu **analisar** , clique em **Configurar análise de código para** *ProjectName*.

3. Nas listas de **configuração** e **plataforma** , clique na configuração de compilação e na plataforma de destino.

4. Para executar a análise de código toda vez que o projeto for criado usando a configuração selecionada, marque a caixa de seleção **Habilitar análise de código na compilação (define CODE_ANALYSIS constante)** . Você também pode executar a análise de código manualmente abrindo o menu **analisar** e clicando em **executar análise de código no** *ProjectName*.

5. Por padrão, a análise de código não relata avisos do código que é gerado automaticamente por ferramentas externas. Para exibir avisos do código gerado, desmarque a caixa de seleção **suprimir resultados do código gerado** .

    > [!NOTE]
    > Essa opção não suprimi erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte de um formulário ou de um modelo.

6. Na lista **executar este conjunto de regras** , siga um destes procedimentos:

    - Clique no conjunto de regras que você deseja usar.

    - Clique **\<Browse...>** para especificar um conjunto de regras personalizadas existente que não esteja na lista.

    - Defina um conjunto de regras personalizadas.

         Para obter mais informações, consulte [criando conjuntos de regras personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Consulte Também
 [Instruções passo a passo: configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
