---
title: 'Como: sincronizar conjuntos de regras do projeto de código com a política de check-in do projeto de equipe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651596"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Como sincronizar conjuntos de regras do projeto de código com política de check-in do projeto da equipe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você sincroniza as configurações de análise de código para projetos de código para a política de check-in do projeto de equipe, especificando um conjunto de regras que contém pelo menos as regras especificadas no conjunto de regras para a política de check-in. O líder do desenvolvedor pode informá-lo sobre o nome e o local do conjunto de regras para a política de check-in. Você pode usar uma das seguintes opções para garantir que a análise de código para o projeto Use o conjunto correto de regras:

- Se a política de check-in usar um dos conjuntos de regras internas da Microsoft, abra a caixa de diálogo Propriedades do projeto de código, exiba a página análise de código e selecione o conjunto de regras na página análise de código das configurações do projeto de código. Os conjuntos de regras padrão da Microsoft são instalados automaticamente com o Visual Studio são definidos como somente leitura e não devem ser editados. Se os conjuntos de regras não forem editados, as regras na política e nos conjuntos de regras locais têm a garantia de haver correspondência.

- Se a política de check-in usar um conjunto de regras personalizado, execute uma operação get no arquivo de conjunto de regras no controle de versão para criar uma cópia local. Em seguida, especifique o local local nas configurações de análise de código para o projeto de código. As regras têm a garantia de corresponder se o conjunto de regras para a política de check-in for atualizado.

     Se você mapear o local do controle de versão para uma pasta local que esteja na mesma relação com a raiz do projeto de equipe como seu projeto de código, o local da regra será definido usando um caminho relativo. O caminho relativo garante que a configuração do projeto de código para análise de código possa ser movida para outros computadores.

- Personalize uma cópia do conjunto de regras para a política de check-in de um projeto de código. Verifique se o novo conjunto de regras contém todas as regras na política de check-in e quaisquer outras regras que você queira incluir. Você deve verificar se o conjunto de regras inclui todas as regras no conjunto de regras para a política de check-in.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar um conjunto de regras padrão da Microsoft

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de código e clique em **Propriedades**.

2. Clique em **análise de código**.

3. Na lista **executar este conjunto de regras** , clique no conjunto de regras da política de check-in.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar um conjunto de regras de política de check-in personalizado

1. Se necessário, execute uma operação get no arquivo de conjunto de regras que especifica a política de check-in.

2. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de código e clique em **Propriedades**.

3. Clique em **análise de código**.

4. Na lista **executar este conjunto de regras** , clique em **\<Browse... >** .

5. Na caixa de diálogo **abrir** , especifique o arquivo de conjunto de regras de política de check-in.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para criar um conjunto de regras personalizado para um projeto de código

1. Siga um dos procedimentos anteriores neste tópico para selecionar a política de check-in do projeto de equipe na página análise de código da caixa de diálogo Configurações do projeto.

2. Clique em **Abrir**.

3. Adicione ou remova regras usando o editor de conjunto de regras.

     Para obter mais informações, consulte [criando conjuntos de regras personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Salve o conjunto de regras modificadas em um arquivo. RuleSet no computador local ou em um caminho UNC.

5. Abra a caixa de diálogo Propriedades do projeto de código e exiba a página de **análise de código** .

6. Na lista **executar este conjunto de regras** , clique em **\<Browse... >** .

7. Na caixa de diálogo **abrir** , especifique o arquivo de conjunto de regras.
