---
title: Suporte de formulário em fluxos de trabalho | Microsoft Docs
description: 'Leia sobre o suporte a formulários em fluxos de trabalho do SharePoint. Quatro tipos de formulários podem ser usados em um fluxo de trabalho: Associação, inicialização, tarefa e modificação.'
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52939fe00dcbca1cfd633c81d4b0a00ea6b517b9
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915499"
---
# <a name="form-support-in-workflows"></a>Suporte de formulário em fluxos de trabalho
  Quatro tipos de formulários podem ser usados em um fluxo de trabalho: Associação, inicialização, tarefa e modificação. Esses tipos de formulário podem ser baseados em um formulário ASPX ou em um formulário do InfoPath. O nível de suporte que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o fornece para um formulário específico depende de vários fatores, que são descritos nas tabelas a seguir. Para obter mais informações sobre tipos de formulário de fluxo de trabalho, consulte [visão geral do Workflow Forms](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refatoração de XML
 Quando você adiciona uma associação ASPX ou um formulário de inicialização a um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] item de projeto de fluxo de trabalho, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o automaticamente refatoria o XML no arquivo de *Elements.xml* do fluxo de trabalho para manter o atributo que se refere ao formulário associação ou inicialização em sincronia sempre que o nome do formulário ou o caminho de implantação é atualizado ou o formulário é excluído. No entanto, quando você usa outros tipos de formulário em um fluxo de trabalho, como um formulário de tarefa ou modificação, o arquivo de *Elements.xml* não é refatorado.

## <a name="form-support-in-new-visual-studio-workflows"></a>Suporte de formulário em novos fluxos de trabalho do Visual Studio
 A tabela a seguir lista o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] suporte para tipos de formulário diferentes em formulários aspx ou InfoPath em fluxos de trabalho que são criados no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo de formulário|Fluxo de trabalho criado no Visual Studio com um formulário ASPX|Fluxo de trabalho criado no Visual Studio usando um formulário do InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Associação|-Um formulário de associação ASPX pode ser adicionado ao fluxo de trabalho usando o modelo de item de **formulário Associação de fluxo de trabalho** .<br />-O arquivo de *Elements.xml* do fluxo de trabalho é refatorado quando o formulário é adicionado, renomeado ou excluído ou quando seu caminho de implantação é alterado.<br />-Para obter mais informações, consulte [Walkthrough: Criando um fluxo de trabalho com formulários de associação e de inicialização](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Não há nenhum modelo de formulário de associação do InfoPath no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Não há integração entre o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o designer do InfoPath.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.|
|Necessária|-Um formulário de inicialização ASPX pode ser adicionado ao fluxo de trabalho usando o modelo de item de **formulário de inicialização do fluxo de trabalho** .<br />-O arquivo de *Elements.xml* do fluxo de trabalho é refatorado quando o formulário é adicionado, renomeado ou excluído ou quando seu caminho de implantação é alterado.<br />-Para obter mais informações, consulte [Walkthrough: Criando um fluxo de trabalho com formulários de associação e de inicialização](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Não há nenhum modelo de formulário de associação do InfoPath no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Não há integração entre o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o designer do InfoPath.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.|
|Tarefa|-Nenhum modelo de formulário de tarefa ASPX está disponível em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Você deve criar uma página de aplicativo e adicionar código a ela.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.<br />-Para obter mais informações, consulte [formulários de tarefas de fluxo de trabalho (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-Não há nenhum modelo de formulário de tarefas do InfoPath no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Não há integração entre o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o designer do InfoPath.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.|
|Modification|-Nenhum modelo de formulário de modificação de ASPX está disponível em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para adicionar um formulário de modificação, você deve criar uma página de aplicativo e adicionar código a ela.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado. Você deve editá-lo manualmente conforme apropriado.<br />-Para obter mais informações, consulte [formulários de modificação de fluxo de trabalho (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-Não há nenhum modelo de formulário de modificação do InfoPath no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Não há integração entre o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o designer do InfoPath.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Suporte ao formulário em fluxos de trabalho reutilizáveis do SharePoint importados
 A tabela a seguir lista o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] suporte para tipos de formulário diferentes em formulários aspx ou InfoPath em fluxos de trabalho reutilizáveis do SharePoint que são importados para o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo de formulário|Fluxo de trabalho reutilizável que tem um formulário ASPX importado do SharePoint Designer|Fluxo de trabalho reutilizável que tem um formulário do InfoPath importado do SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Associação|-O formulário é referenciado no arquivo de *Elements.xml* do fluxo de trabalho.<br />-O arquivo de *Elements.xml* do fluxo de trabalho é refatorado quando o formulário é renomeado ou excluído ou quando seu caminho de implantação é alterado.|-O formulário é importado, mas não é referenciado no *Elements.xml* do fluxo de trabalho.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.|
|Necessária|-O formulário é referenciado pelo fluxo de trabalho no arquivo de *Elements.xml* do fluxo de trabalho.<br />-O arquivo de *Elements.xml* do fluxo de trabalho é refatorado quando o formulário é renomeado ou excluído ou quando seu caminho de implantação é alterado.|-O formulário é importado, mas não é referenciado no *Elements.xml* do fluxo de trabalho.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado. **Observação:**  Regras e propriedades devem ser adicionadas e alteradas para que esse cenário funcione.|
|Tarefa|-O formulário é referenciado no arquivo de *Elements.xml* do fluxo de trabalho.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado.|-O formulário é importado, mas não é referenciado no *Elements.xml* do fluxo de trabalho.<br />-O arquivo de *Elements.xml* do fluxo de trabalho não é refatorado. **Observação:**  Regras e propriedades devem ser adicionadas e alteradas para que esse cenário funcione.|
|Modification|Não aplicável. Não é possível criar formulários de modificação ASPX no SharePoint Designer.|Não aplicável. Os formulários de modificação do InfoPath não podem ser criados no SharePoint Designer, exceto para o fluxo de trabalho interno do SharePoint Server, que não está incluído no arquivo. wsp quando o fluxo de trabalho é exportado.|

## <a name="see-also"></a>Confira também
- [Walkthrough: criar um fluxo de trabalho com formulários de associação e de inicialização](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Criar soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importar itens de um site existente do SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
