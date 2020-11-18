---
title: Como adicionar um arquivo de recurso | Microsoft Docs
description: Adicione um arquivo de recurso no Visual Studio, usando comandos no menu de atalho do nó da solução e nós de recurso no Gerenciador de Soluções.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 440777aaaf239dcdd3c276786a82e3d8aef55070
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850124"
---
# <a name="how-to-add-a-resource-file"></a>Como adicionar um arquivo de recurso
  Os comandos para adicionar arquivos de recurso estão no menu de atalho do nó da solução e nós de recurso no Gerenciador de Soluções. Para obter mais informações, consulte [localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Para adicionar um arquivo de recurso global a uma solução do SharePoint

1. No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , abra uma solução do SharePoint.

2. Em **Gerenciador de soluções**, escolha um nó de projeto do SharePoint e, na barra de menus, escolha **projeto**  >  **Adicionar novo item**.

3. Na caixa de diálogo **Adicionar novo item** , escolha o modelo de **arquivo recursos globais** e, em seguida, escolha o botão **Adicionar** .

   > [!NOTE]
   > O modelo de item de projeto de arquivo de recursos globais aparece somente quando um item de projeto do SharePoint é selecionado.

4. Na caixa de diálogo **Adicionar recurso** , escolha uma cultura para o arquivo de recurso, como inglês (Estados Unidos).

    Esta etapa adiciona um arquivo de recurso global à sua solução no formato Resource_x_ **.** <em>cultura</em><strong>.</strong> resx, como, *recurso1. en-US. resx*.

5. Quando o **Editor de recursos** for aberto no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , adicione recursos ao arquivo de recurso.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Para adicionar um arquivo de recursos de recurso a um recurso do SharePoint

1. Se a solução do SharePoint ainda não estiver aberta no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , abra a solução.

2. No **Gerenciador de soluções**, abra o menu de atalho para o nome de um recurso no nó **recursos** e escolha **Adicionar recurso**.

     Esta etapa adiciona um arquivo de recurso ao recurso no formato _resourceFileName_**.** _Culture_**. resx**, como, *Feature1. en-US. resx*.

3. Quando o **Editor de recursos** for aberto no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , adicione recursos ao arquivo de recurso.

## <a name="see-also"></a>Confira também
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
