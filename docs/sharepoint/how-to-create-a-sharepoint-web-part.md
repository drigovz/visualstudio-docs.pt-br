---
title: 'Como: Criar uma Web Part do SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 43d776a4031cabfd027c96105f3e71a93ea1c07f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858417"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Como: Criar uma web part do SharePoint
  Você pode criar e personalizar uma web part adicionando um **Web Part** de item para qualquer projeto do SharePoint e, em seguida, editando o arquivo de código para a web part ou usando um designer. Para obter mais informações, confira [Como: Criar uma web part do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Para criar uma web part do SharePoint
  
1.  Crie ou abra um projeto do SharePoint.  
  
     Para obter mais informações, consulte [SharePoint modelos de item de projeto e projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Escolha o nó de projeto do SharePoint no **Gerenciador de soluções** e, em seguida, escolha **Project** > **Add New Item**.  
  
3.  No **Adicionar Novo Item** diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  Na lista de modelos do SharePoint, escolha **Web Part**.  
  
5.  No **nome** caixa, especifique um nome para a web part e, em seguida, escolha o **Add** botão.  
  
     A web part aparece na **Gerenciador de soluções**. Para obter mais informações sobre os arquivos que inclui uma web part, consulte [criar web parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  Na **Gerenciador de soluções**, abra o arquivo de código para a web part que você acabou de criar.  
  
     Por exemplo, se for o nome da sua web part *WebPart1*, abra *WebPart1.vb* (no Visual Basic) ou *WebPart1.cs* (em c#).  
  
7.  O arquivo de código, adicionar controles para o <xref:System.Web.UI.Control.CreateChildControls%2A> método.  
  
     Por exemplo, consulte [passo a passo: Criar uma web part do SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Consulte também
 [Criar web parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Como: Criar uma web part do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Passo a passo: Criar uma web part do SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Passo a passo: Criar uma web part para SharePoint usando um designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
