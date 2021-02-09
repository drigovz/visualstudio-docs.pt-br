---
title: 'Como: criar uma Web Part do SharePoint usando um designer | Microsoft Docs'
titleSuffix: ''
description: Crie uma Web Part adicionando um item de Web Part Visual a um projeto do SharePoint, que abre o designer do Visual Web Developer no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14f6add337ecfae3ab0dc5aa77a72962f2a0a915
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851589"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Como: criar uma Web Part do SharePoint usando um designer
  Você pode criar uma Web Part adicionando um item de **Web Part Visual** a qualquer projeto do SharePoint. Isso abre o designer do Visual Web Developer no Visual Studio, no qual você pode adicionar controles e código à Web Part. As Web Parts visuais funcionam da mesma forma que as Web Parts. A única diferença é que você cria Web Parts visuais no designer do Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Para criar um projeto para Web Parts visuais

1. Na barra de menus, escolha **arquivo**  > **novo**  >  **projeto**.

     A caixa de diálogo **Novo Projeto** será aberta.

2. Na caixa de diálogo **novo projeto** , em **Visual C#** ou **Visual Basic**, expanda o nó **Office/SharePoint** e escolha a categoria **soluções do SharePoint** .

3. Na lista de modelos de projeto, escolha **SharePoint 2013-Web Part Visual** e, em seguida, escolha o botão **OK** .

     O **Assistente para personalização do SharePoint** é exibido.

4. Na página **especificar o site e o nível de segurança para depuração** , ESPECIFIQUE a URL de um site do SharePoint que está no computador local e, em seguida, escolha o botão **concluir** .

     No **Gerenciador de soluções**, uma Web Part é exibida. Depois de criar a Web Part no designer do Visual Web Developer, você o testará no site que você especificar.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Para adicionar uma Web Part Visual a um projeto existente do SharePoint

1. Na barra de menus, escolha **projeto**  >  **Adicionar novo item**.

2. Na caixa de diálogo **Adicionar novo item** , escolha o nó **Office/SharePoint** .

3. Na lista de modelos de projeto, escolha **Visual Web Part**, nomeie-o e, em seguida, escolha o botão **Adicionar** .

     No **Gerenciador de soluções**, sua Web Part é exibida. Depois de criar a Web Part no designer do Visual Web Developer, você o testará no site que você especificar.

## <a name="see-also"></a>Consulte também
- [Criar Web Parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Como: criar uma Web Part do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Walkthrough: criar uma Web Part para o SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Walkthrough: criar uma Web Part para o SharePoint usando um designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
