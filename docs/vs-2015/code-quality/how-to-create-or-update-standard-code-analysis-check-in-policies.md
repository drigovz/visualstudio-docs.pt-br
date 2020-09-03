---
title: 'Como: criar ou atualizar políticas de check-in de análise de código padrão | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661771"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Como criar ou atualizar políticas de check-in de análise do código padrão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode exigir que a análise de código seja executada em todos os projetos de código em um projeto de equipe usando a política de check-in de análise de código. Exigir análise de código pode melhorar a qualidade do código que é verificado na base de código.

> [!NOTE]
> Esse recurso estará disponível somente se você estiver usando Team Foundation Server.

 As políticas de check-in de análise de código são definidas nas configurações do projeto de equipe e se aplicam a cada projeto de código no projeto de equipe. As execuções de análise de código são configuradas para projetos de código no arquivo de projeto (. xxproj) para o projeto de código. As execuções de análise de código são executadas no computador local. Quando você habilita uma política de check-in de análise de código, os arquivos em um projeto de código que deverão ser verificados devem ser compilados após a última edição e uma execução de análise de código que contém, no mínimo, as regras nas configurações do projeto de equipe devem ser executadas no computador onde as alterações foram feitas.

- Para código gerenciado, você define a política de check-in especificando um *conjunto de regras* que contém um subconjunto das regras de análise de código.

- Para código C/C++, a política de check-in requer que todas as regras de análise de código sejam executadas. Você pode adicionar diretivas de pré-processador para desabilitar regras específicas para os projetos de código individuais em seu projeto de equipe.

  Depois de especificar uma política de check-in para código gerenciado, os integrantes da equipe podem sincronizar suas configurações de análise de código para projetos de código para as configurações de política do projeto de equipe.

### <a name="to-open-the-check-in-policy-editor"></a>Para abrir o editor de diretiva de check-in

1. Em Team Explorer, clique com o botão direito do mouse no nome do projeto de equipe, aponte para **configurações do projeto de equipe**e clique em controle do **código-fonte**.

2. Na caixa de diálogo **controle do código-fonte** , selecione a guia **política de check-in** .

3. Realize um dos seguintes procedimentos:

    - Clique em **Adicionar** para criar uma nova política de check-in.

    - Clique duas vezes no item **análise de código** existente na lista **tipo de política** para alterar a política.

### <a name="to-set-policy-options"></a>Para definir opções de política

- Marque ou desmarque as seguintes opções:

    |Opção|Descrição|
    |------------|-----------------|
    |**Impor check-in para conter somente arquivos que fazem parte da solução atual.**|A análise de código pode ser executada somente em arquivos especificados nos arquivos de configuração da solução e do projeto. Essa política garante que todo o código que faz parte de uma solução seja analisado.|
    |**Impor análise de código C/C++ (/Analyze)**|Requer que todos os projetos C ou C++ sejam compilados com a opção de compilador/analyze para executar a análise de código antes que eles possam ser verificados.|
    |**Impor análise de código para código gerenciado**|Requer que todos os projetos gerenciados executem a análise de código e compilem antes que possam ser verificados.|

-

### <a name="to-specify-a-managed-rule-set"></a>Para especificar um conjunto de regras gerenciadas

- Na lista **executar este conjunto de regras** , use um dos seguintes métodos:

  - Selecione um conjunto de regras padrão da Microsoft.

  - Para selecionar um conjunto de regras personalizado, clique em **\<Select Rule Set from Source Control...>** e digite o caminho de controle de versão do conjunto de regras no navegador de controle do código-fonte. A sintaxe de um caminho de controle de versão é:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Para obter mais informações sobre como criar e implementar um conjunto de regras de política de check-in personalizado, consulte [implementando políticas de check-in personalizadas para código gerenciado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Consulte Também
 [Criando e usando políticas de check-in de análise do código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
