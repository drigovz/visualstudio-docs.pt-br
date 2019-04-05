---
title: 'Como: Especificar conjuntos de regras de código gerenciado para vários projetos em uma solução | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2bf83c66f86d516d18221d01470e125979d39349
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922683"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Como: Especificar conjuntos de regras de código gerenciado para vários projetos em uma solução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, todos os projetos gerenciados de uma solução são atribuídos a análise de código Microsoft mínimo recomendado regras *conjunto de regras*. Você pode alterar os conjuntos de regras que são atribuídos aos projetos de uma solução na caixa de diálogo Propriedades da solução.  
  
> [!NOTE]
>  Por padrão, a análise de código do projeto não é executada como uma etapa de compilação. Para habilitar a análise de código como uma etapa de compilação, consulte [como: Configurar análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Para especificar uma regra definida para vários projetos em uma solução de código gerenciado  
  
1.  No [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], ou [!INCLUDE[vsPro](../includes/vspro-md.md)] abra a solução.  
  
2.  Sobre o **Analyze** menu, clique em **configurar a análise de código para solução**.  
  
3.  Se necessário, expanda **propriedades comuns**e, em seguida, clique em **configurações de análise de código**.  
  
4.  Você pode especificar uma regra definida para um ou mais projetos.  
  
    -   Para especificar uma regra definida para um projeto individual, clique no nome do projeto.  
  
    -   Para especificar uma regra definida para vários projetos, mantenha pressionada a tecla CTRL e clique nos nomes de projeto.  
  
    -   Para especificar todos os projetos na solução, mantenha pressionada a tecla SHIFT e clique na lista de projetos.  
  
5.  Clique o **do conjunto de regras** campo de um projeto e, em seguida, clique o nome da regra de conjunto que você deseja aplicar.
