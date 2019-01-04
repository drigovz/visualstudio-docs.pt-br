---
title: 'Como: Criar uma Web Part do SharePoint usando um Designer | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55104f4e1728208c93dc80080a42059963e3c7a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858442"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Como: Criar uma Web Part do SharePoint usando um designer
  Você pode criar uma web part, adicionando um **Web Part Visual** item para qualquer projeto do SharePoint. Isso abre o designer do Visual Web Developer no Visual Studio, onde você pode adicionar controles e código para a web part. Web parts visuais funcionam da mesma forma como partes da web. A única diferença é que você criar web parts visuais no designer do Visual Web Developer.  
  
### <a name="to-create-a-project-for-visual-web-parts"></a>Para criar um projeto de web parts visuais  
  
1.  Na barra de menus, selecione **Arquivo** >**Novo** > **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
2.  No **novo projeto** caixa de diálogo, em qualquer um **Visual c#** ou **Visual Basic**, expanda o **Office/SharePoint** nó e, em seguida, escolha o **soluções do SharePoint** categoria.  
  
3.  Na lista de modelos de projeto, escolha **SharePoint 2013 - Web Part Visual**e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente para personalização do SharePoint** é exibida.  
  
4.  Sobre o **especificar o nível de site e segurança para depuração** da página, especifique a URL de um site do SharePoint que está no computador local, e, em seguida, escolha o **concluir** botão.  
  
     Na **Gerenciador de soluções**, uma web part é exibida. Depois de criar a web part no designer do Visual Web Developer, você vai testá-lo no site que você especificar.  
  
### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Para adicionar uma web part visual a um projeto existente do SharePoint  
  
1.  Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** diálogo caixa, escolha o **Office/SharePoint** nó.  
  
3.  Na lista de modelos de projeto, escolha **Web Part Visual**, nomeie-o e, em seguida, escolha o **Add** botão.  
  
     Na **Gerenciador de soluções**, sua web part é exibida. Depois de criar a web part no designer do Visual Web Developer, você vai testá-lo no site que você especificar.  
  
## <a name="see-also"></a>Consulte também
 [Criar web parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Como: Criar uma web part do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Passo a passo: Criar uma web part do SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Passo a passo: Criar uma web part para SharePoint usando um designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
