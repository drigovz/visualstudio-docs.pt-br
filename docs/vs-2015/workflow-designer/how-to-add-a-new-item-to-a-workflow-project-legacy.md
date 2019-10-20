---
title: 'Como: adicionar um novo item a um projeto de fluxo de trabalho (Herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46f6e9daafc2688b9bea75cba9eddd8c8a53c9bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656665"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Como: Adicionar um novo item em um fluxo de trabalho Project (o legados)
Depois de criar um projeto de fluxo de trabalho usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)] que tem como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], você pode adicionar itens de [!INCLUDE[wf](../includes/wf-md.md)] e outros itens de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] familiares ao seu projeto.

 A tabela a seguir lista os itens de [!INCLUDE[wf2](../includes/wf2-md.md)] que você pode adicionar a um projeto de fluxo de trabalho.

|Item|Descrição|
|----------|-----------------|
|Atividade|Uma atividade com a definição de atividade em um código de arquivo e de usuário do designer de código em um código separado arquivos.|
|Atividade (com separação de código)|Uma definição de atividade expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado código.|
|Fluxo de trabalho sequencial (código)|Um trabalho sequenciais com a definição de trabalho em um código de arquivo e de usuário do designer de código em um arquivo separado código.|
|Fluxo de trabalho sequencial (com separação de código)|Um trabalho sequenciais com a definição de trabalho expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado código.|
|Fluxo de trabalho do computador de estado (código)|Um trabalho do computador de estado com a definição de trabalho em um código de arquivo e de usuário do designer de código em um arquivo separado código.|
|Fluxo de trabalho do computador de estado (com separação de código)|Um trabalho do computador de estado com a definição de trabalho expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado código.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para adicionar um novo item em um fluxo de trabalho projeto

1. No menu **projeto** , clique em **Adicionar um novo item**.

     A caixa de diálogo **Adicionar um novo item** é aberta.

2. Selecione um item.

     A tabela anterior lista opções disponíveis do Windows Workflow Foundation.

3. Clique em **Adicionar** para adicionar o item ao projeto de fluxo de trabalho.

## <a name="see-also"></a>Consulte também
 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)