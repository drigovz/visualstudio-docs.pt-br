---
title: Usando o designer de atividades herdadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cd8d18d95fabd858354c625d2c9b32459efc7193
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846148"
---
# <a name="using-the-legacy-activity-designer"></a>Usando o designer herdado de atividades
Este tópico descreve como usar o designer de atividade em [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use o designer herdado na definição [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 O designer de atividade permite que você crie suas próprias atividades personalizados.

## <a name="creating-a-custom-activity"></a>Criando uma atividade personalizado
 Siga estas etapas para criar uma atividade personalizado utilizando o designer de atividade:

1. No menu **projeto** , clique em **Adicionar atividade**.

2. Selecione o modelo **atividade** ou **atividade (com separação de código)** .

   1. Use o modelo de **atividade** para criar uma atividade com a definição da atividade e o código do usuário no mesmo arquivo de código.

   2. Use o modelo **atividade (com separação de código)** para criar uma atividade com a definição de atividade expressa como marcação de fluxo de trabalho e o código de usuário em um arquivo de código separado.

3. Digite um nome de atividade ou mantenha o nome padrão e clique em **Adicionar**.

   Você também pode criar um conjunto de atividades personalizadas criando um novo projeto do tipo **biblioteca de atividades de fluxo de trabalho**. Para obter mais informações sobre esse tipo de projeto, consulte [como: criar uma biblioteca de atividades de fluxo de trabalho (Herdado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configurando uma atividade
 Quando o designer de atividade estiver ativo, você pode usar o navegador de propriedade para configurar as propriedades listadas na tabela a seguir.

|propriedade|Comments|
|--------------|--------------|
|**Nome**|Nome da atividade.|
|**Classe base**|Classe base que a atividade deriva. A classe base padrão é [SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx). Na janela **Propriedades** , clique nas reticências da **classe base** **[...]** para selecionar outra classe base na [caixa de diálogo Procurar e selecione um tipo .net (Herdado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Descrição**|Descrição definido pelo usuário de atividade.|
|**Habilitado**|Defina como **true** por padrão para habilitar a execução e a validação da atividade. Defina como **false** para desabilitar a execução e a validação da atividade. Para obter informações sobre a execução e a validação da atividade, consulte [desenvolvendo atividades de fluxo de trabalho](https://msdn2.microsoft.com/library/ms734413.aspx).|

## <a name="adding-child-activities"></a>Adicionando atividades filhos
 Você pode arrastar atividades filhos da caixa de ferramentas para a atividade que você está criando. Você pode então configurar cada atividade filho usando o navegador de propriedade.

## <a name="see-also"></a>Veja também
 [Desenvolvendo atividades de fluxo de trabalho](https://msdn2.microsoft.com/library/ms734413.aspx) [criando atividades personalizadas](https://msdn2.microsoft.com/library/bb675228.aspx) atividades de [fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md) atividades [personalizadas exemplo](https://msdn2.microsoft.com/library/bb472471.aspx) [: como criar uma biblioteca de atividades de fluxo de trabalho (herdada)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [usando o designer de fluxo de trabalho herdado](../workflow-designer/using-the-legacy-workflow-designer.md)
