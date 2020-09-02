---
title: Como especificar um nome do menu Iniciar para um aplicativo ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149766"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Como especificar um nome no menu Iniciar para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo é instalado para uso online e offline, uma entrada é adicionada ao menu **Iniciar** e à lista **Adicionar ou remover programas** . Por padrão, o nome de exibição é o mesmo que o nome do assembly do aplicativo, mas você pode alterar o nome de exibição definindo o **nome do produto** na caixa de diálogo **Opções de publicação** .  
  
 O **nome do produto** será exibido na página publish.htm; para um aplicativo offline instalado, ele será o nome da entrada no menu **Iniciar** e também será o nome exibido em **Adicionar ou remover programas**.  
  
 O **nome do editor** será exibido na página de publish.htm acima do nome do **produto**e, para um aplicativo offline instalado, ele também será o nome da pasta que contém o ícone do aplicativo no menu **Iniciar** .  
  
 Você pode definir as **Propriedades nome do produto** e nome do **Editor** na caixa de diálogo **Opções de publicação** , disponível na página **publicar** do **Designer de projeto**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar um nome do menu iniciar  
  
1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.  
  
2. Clique na guia **Publicar**.  
  
3. Clique no botão **Opções** para abrir a caixa de diálogo **Opções de publicação** .  
  
4. Clique em **Descrição**.  
  
5. Na caixa de diálogo **Opções de publicação** , digite o nome a ser exibido no **nome do produto**.  
  
6. Opcionalmente, você pode inserir um nome de editor no **nome do editor**.  
  
## <a name="see-also"></a>Consulte Também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
