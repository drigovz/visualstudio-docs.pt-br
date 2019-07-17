---
title: 'Como: Especifique uma página de publicação para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202169"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Como: Especificar uma página de publicação para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo, uma página de Web padrão (Publish. htm) é gerada e publicada com o aplicativo. Esta página contém o nome do aplicativo, um link para instalar o aplicativo e/ou em todos os pré-requisitos e um link para um tópico da Ajuda que descreve [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. O **página de publicação** propriedade para o seu projeto permite que você especifique um nome para a página da Web para seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo.  
  
 Depois que a página de publicação tiver sido especificada, na próxima vez que você publica, ele será copiado para o local de publicação; ele não será substituído se você publicar novamente. Se você quiser personalizar a aparência da página, você pode fazer isso sem se preocupar sobre perder suas alterações. Para obter mais informações, confira [Como: Personalizar a página da Web padrão do ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 O **página publicar** propriedade pode ser definida **opções de publicação** caixa de diálogo, acessível a partir o **publicar** painel do **Project Designer**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Para especificar uma página da Web personalizada para um aplicativo ClickOnce  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Selecione o **publicar** painel.  
  
3. Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4. Clique em **implantação**.  
  
5. No **opções de publicação** diálogo caixa, certifique-se de que o **página da web de implantação aberto depois de publicar** caixa de seleção está selecionada (ela deve ser selecionada por padrão).  
  
6. No **página da web de implantação:** caixa, digite o nome da página da Web e, em seguida, clique em **Okey**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Para impedir que a página publish Inicie cada vez que você publicar  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Selecione o **publicar** painel.  
  
3. Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4. Clique em **implantação**.  
  
5. No **opções de publicação** caixa de diálogo, desmarque a **página da web de implantação aberto depois de publicar** caixa de seleção.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Como: Personalizar a página da Web padrão do ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
