---
title: Diretrizes para importar fluxos de trabalho reutilizáveis | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb386a2d80931ece415b0b3939f2947678808261
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557108"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Diretrizes para importar fluxos de trabalho reutilizáveis
  Para importar fluxos de trabalho reutilizáveis criados no SharePoint Designer, use o modelo de projeto importar fluxo de trabalho do SharePoint 2010 de importação reutilizável no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Esse modelo importa um *fluxo de trabalho* *declarativo* ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] somente) e o converte em um *fluxo de trabalho de código*, que é um fluxo de trabalho que você pode aprimorar com um ou um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] código. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Walkthrough: importar um fluxo de trabalho reutilizável do SharePoint Designer para o Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 No entanto, o modelo importar fluxo de trabalho do SharePoint 2010 reutilizável pode importar somente soluções de farm. Se você quiser implantar seu fluxo de trabalho como uma solução de área restrita, importe-o com o modelo importar pacote de solução do SharePoint 2010. No entanto, ao fazer isso, você não pode convertê-lo no fluxo de trabalho de código e não poderá modificá-lo como tal.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importar fluxos de trabalho reutilizáveis usando o modelo importar fluxo de trabalho reutilizável
 Se você importar um fluxo de trabalho reutilizável usando o modelo importar fluxo de trabalho do SharePoint 2010 reutilizável, poderá executar ou alterar a solução assim como qualquer outra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solução do SharePoint, mas poderá ser necessário corrigir alguns itens manualmente.

### <a name="import-task-forms"></a>Importar formulários de tarefas
 O modelo de projeto importar fluxo de trabalho do SharePoint 2010 de importação importa todos os formulários de inicialização e associação, mas importa apenas um formulário de tarefa porque o esquema do fluxo de trabalho do código só permite um formulário de tarefa. Todos os formulários de tarefa adicionais da solução de fluxo de trabalho original são colocados na pasta **outros arquivos importados** no **Gerenciador de soluções**.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importar fluxos de trabalho reutilizáveis usando o modelo de pacote de solução importar SharePoint 2010
 Se você importar um fluxo de trabalho reutilizável usando o modelo de pacote de solução importar SharePoint 2010, precisará considerar os seguintes problemas:

- Depois de importar o fluxo de trabalho, você pode implantá-lo e executá-lo imediatamente no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] escolhendo a tecla **F5** . No entanto, se você alterar alguma coisa no fluxo de trabalho na solução importada, poderá ser necessário corrigir manualmente os elementos no projeto antes de implantar e executar o fluxo de trabalho.

- Como o fluxo de trabalho é declarativo, o código não pode ser adicionado a ele. Para converter o fluxo de trabalho em um fluxo de trabalho de código, você deve importá-lo no usando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o modelo importar fluxo de trabalho do SharePoint 2010 reutilizável.

- Embora seja possível editar o arquivo do designer de fluxo de trabalho (. xoml) no modo de exibição de Design, é recomendável editá-lo no modo de exibição de origem, pois o designer de fluxo de trabalho exibe erros falsos.

- A depuração no fluxo de trabalho não funciona para conteúdo declarativo. Os pontos de interrupção definidos em [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] não são atingidos.

## <a name="import-globally-reusable-workflow-solutions"></a>Importar soluções de fluxo de trabalho reutilizáveis globalmente
 Fluxos de trabalho reutilizáveis globalmente não podem ser importados usando o modelo importar fluxo de trabalho do SharePoint 2010 reutilizável. Para importar um fluxo de trabalho reutilizável globalmente, você precisa convertê-lo em um fluxo de trabalho reutilizável não globalmente ou você precisa usar o modelo de pacote de solução importar SharePoint 2010.

 Para converter o fluxo de trabalho, faça uma cópia do fluxo de trabalho reutilizável globalmente no SharePoint Designer (abrindo o menu de atalho para o fluxo de trabalho e escolhendo **salvar como cópia**). Em seguida, importe o novo fluxo de trabalho reutilizável com o modelo importar fluxo de trabalho do SharePoint 2010 reutilizável no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Para importar o fluxo de trabalho reutilizável globalmente sem modificá-lo, use o modelo importar pacote de solução do SharePoint 2010. Se você usar esse método, o fluxo de trabalho não será convertido em um fluxo de trabalho de código e permanecerá um fluxo de trabalho declarativo.

## <a name="see-also"></a>Confira também
- [Importar itens de um site existente do SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Walkthrough: importar um fluxo de trabalho reutilizável do SharePoint Designer para o Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
