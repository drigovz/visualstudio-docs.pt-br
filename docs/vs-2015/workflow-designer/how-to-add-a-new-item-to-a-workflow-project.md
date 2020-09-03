---
title: 'Como: adicionar um novo item a um projeto de fluxo de trabalho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656627"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Como: Adicionar um novo item em um fluxo de trabalho Projeto
Depois de criar um projeto de fluxo de trabalho, você pode adicionar atividades de fluxo de trabalho, designer, e outros itens de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] familiares ao seu projeto.

 A tabela a seguir lista os itens de [!INCLUDE[wf](../includes/wf-md.md)] que você pode adicionar a um projeto de fluxo de trabalho.

|Name|Descrição|
|----------|-----------------|
|Atividade|Uma atividade a ser composta de outras atividades. A seleção deste item adiciona o mesmo arquivo XAML ao projeto, como você obteria ao selecionar o modelo de **biblioteca de atividades** para um novo projeto. [!INCLUDE[crabout](../includes/crabout-md.md)] neste procedimento, consulte [como: criar uma biblioteca de atividades](../workflow-designer/how-to-create-an-activity-library.md).|
|Designer de Activity|Um designer para personalizar a experiência em tempo de design de uma atividade. A seleção deste item adiciona os mesmos arquivos ao projeto, como você obteria ao selecionar o modelo de **biblioteca do designer de atividade** para um novo projeto. [!INCLUDE[crabout](../includes/crabout-md.md)] neste procedimento, consulte [como criar uma biblioteca do designer de atividade](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Atividade do código|Uma atividade com a lógica de execução gravar no código. Um arquivo de código-fonte com uma substituição do método de <xref:System.Activities.CodeActivity.Execute%2A> é gerado para você.|
|WCF Serviço de Fluxo de Trabalho|Um serviço de [!INCLUDE[indigo2](../includes/indigo2-md.md)] compilado usando atividades de fluxo de trabalho. A seleção deste item adiciona os mesmos arquivos ao projeto, como você obteria ao selecionar o modelo de **aplicativo do serviço de fluxo de trabalho WCF** para um novo projeto. [!INCLUDE[crabout](../includes/crabout-md.md)] sobre este procedimento, consulte [como criar um aplicativo de serviço de fluxo de trabalho WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para adicionar um novo item em um fluxo de trabalho projeto

1. No menu **projeto** , clique em **Adicionar novo item...**.

     A caixa de diálogo **Adicionar um novo item** é aberta.

2. No painel **modelos instalados** , selecione grupo de **fluxos de trabalho** .

3. Selecione um dos quatro itens. A tabela anterior lista as seleções disponíveis.

4. Digite um nome apropriado para o item na caixa **nome** na parte inferior da caixa de diálogo.

5. Clique em **Adicionar** para adicionar o item ao projeto de fluxo de trabalho atual.

## <a name="see-also"></a>Consulte Também
 [Criando um fluxo de trabalho Projeto](../workflow-designer/creating-a-workflow-project.md)