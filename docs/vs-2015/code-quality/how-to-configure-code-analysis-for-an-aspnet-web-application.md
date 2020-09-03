---
title: 'Como: configurar a análise de código para um aplicativo Web ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657456"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Como configurar a análise de código para um aplicativo Web do ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] você pode selecionar em uma lista de conjuntos de *regras* de análise de código para aplicar ao [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicativo Web. O conjunto de regras padrão é as regras recomendadas do Microsoft Mininimum. Você pode selecionar outro conjunto de regras para aplicar ao site.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Para configurar um conjunto de regras para um projeto de estrutura de página ASP.NET

1. Selecione o site da Web no **Gerenciador de soluções**.

2. No menu **analisar** , clique em **Configurar análise de código para o site**.

3. Se você selecionou a solução e a solução tiver mais de um projeto, selecione o sistema operacional de configuração e destino de compilação nas listas de **configuração** e **plataforma** .

4. Para cada projeto na solução, clique na coluna **conjunto de regras** e, em seguida, clique no nome do conjunto de regras a ser executado.

5. Por padrão, a análise de código é executada em todos os projetos na solução. Para desabilitar ou habilitar a análise de código para um projeto específico, siga estas etapas:

    1. Clique com o botão direito do mouse no nome do projeto e clique em Propriedades.

    2. Marque ou desmarque a caixa de seleção **Habilitar análise de código** . Você também pode executar a análise de código manualmente selecionando **executar análise de código no site** no menu **analisar** .

6. Na lista suspensa **executar esta regra definida** , siga estas etapas:

    - Selecione o conjunto de regras que você deseja usar.

    - Selecione **\<Browse>** para especificar um conjunto de regras personalizadas existente que não esteja na lista.

    - Defina um conjunto de regras personalizadas. Para obter mais informações, consulte [criando conjuntos de regras personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).
