---
title: Como especificar conjuntos de regras de código gerenciado para vários projetos em uma solução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656419"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Como especificar conjuntos de regras de código gerenciado para vários projetos em uma solução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, todos os projetos gerenciados de uma solução são atribuídos ao *conjunto*de regras de análise de código de regras recomendadas mínimas da Microsoft. Você pode alterar os conjuntos de regras que são atribuídos aos projetos de uma solução na caixa de diálogo Propriedades da solução.

> [!NOTE]
> Por padrão, a análise de código do projeto não é executada como uma etapa de compilação. Para habilitar a análise de código como uma etapa de compilação, consulte [como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Para especificar um conjunto de regras para vários projetos em uma solução de código gerenciado

1. Em [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] . [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]ou [!INCLUDE[vsPro](../includes/vspro-md.md)] abra a solução.

2. No menu **analisar** , clique em **Configurar análise de código para solução**.

3. Se necessário, expanda **Propriedades comuns**e clique em **configurações de análise de código**.

4. Você pode especificar um conjunto de regras para um ou mais projetos.

    - Para especificar um conjunto de regras para um projeto individual, clique no nome do projeto.

    - Para especificar um conjunto de regras para vários projetos, mantenha a tecla CTRL pressionada e clique nos nomes do projeto.

    - Para especificar todos os projetos na solução, mantenha pressionada a tecla SHIFT e clique na lista projeto.

5. Clique no campo **conjunto de regras** de um projeto e, em seguida, clique no nome do conjunto de regras que você deseja aplicar.
