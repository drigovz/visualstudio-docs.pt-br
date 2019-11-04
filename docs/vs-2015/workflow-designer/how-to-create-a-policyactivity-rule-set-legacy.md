---
title: 'Como: Criar um conjunto de regras PolicyActivity (Herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c200c7db90f3cad12c1188af88f4651d2f2d44c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663386"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Como: Criar uma regra de PolicyActivity definida (herdado)
Este tópico descreve como criar um conjunto de regras de atividade de política usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Depois de arrastar um item de atividade de **política** da **caixa de ferramentas** para a superfície de design do fluxo de trabalho, você desejará selecionar uma regra existente ou criar um novo conjunto de regras para a atividade [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) . Selecione um conjunto de regras existente usando a [caixa de diálogo Selecionar conjunto de regras (Herdado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e crie conjuntos de regras usando a [caixa de diálogo Editor de conjunto de regras (Herdado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Você pode abrir a caixa de diálogo [Editor de conjunto de regras (Herdado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) diretamente clicando duas vezes em uma atividade [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) que está na superfície de design do fluxo de trabalho.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Para selecionar ou criar uma regra definida para uma atividade de PolicyActivity

1. Clique com o botão direito do mouse no [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)e clique em **Propriedades** para abrir a janela **Propriedades** .

2. Clique na propriedade **RuleSetReference** .

3. Realize um dos seguintes procedimentos:

    - Clique nas reticências RuleSetReference **[...]** e selecione um conjunto de regras existente na caixa de [diálogo Selecionar conjunto de regras (Herdado)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Então vá para a etapa 10.

         - ou -

    - Digite um nome para um conjunto de regras. Clique nas reticências RuleSetReference **[...]** e, em seguida, selecione **Editar** na [caixa de diálogo Selecionar conjunto de regras (Herdado)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         - ou -

    - Digite um nome para um conjunto de regras. Expanda a propriedade **RuleSetReference** e selecione as reticências **[...]** na propriedade de definição do conjunto de **regras** .

         A [caixa de diálogo Editor de conjunto de regras (Herdado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) é aberta.

4. Na [caixa de diálogo Editor de conjunto de regras (Herdado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), clique em **Adicionar regra** para adicionar uma nova regra ao conjunto de regras.

5. Insira o **nome**, a **prioridade**e as propriedades de **reavaliação** ou mantenha os valores padrão.

6. Insira o texto para a **condição**.

7. Insira o texto para as **ações then** e **outras ações**.

8. Clique em **Adicionar regra** novamente para adicionar outra regra.

9. Ao terminar, clique em **OK**.

## <a name="see-also"></a>Consulte também
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) [Caixa de diálogo selecionar conjunto de regras (Herdado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [caixa de diálogo Editor de conjunto de regras (Herdado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [usando a atividade de política](http://go.microsoft.com/fwlink?LinkID=65004) [atividades herdadas de fluxo de trabalho](../workflow-designer/legacy-workflow-activities.md)