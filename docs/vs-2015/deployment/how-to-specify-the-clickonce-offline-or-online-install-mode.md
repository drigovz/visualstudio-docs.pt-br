---
title: 'Como: Especifique o ClickOnce Offline ou Online de modo de instalação | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149753"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Como: Especificar o modo de instalação offline ou online do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O `Install Mode` para um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo determina se o aplicativo estará disponível offline ou online. Quando você escolhe **o aplicativo está disponível somente online**, o usuário deve ter acesso para o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] local (uma página da Web ou um compartilhamento de arquivos) para executar o aplicativo de publicação. Quando você escolhe **o aplicativo está disponível também offline**, o aplicativo adiciona entradas para o **inicie** menu e o **adicionar ou remover programas** caixa de diálogo; o usuário é é possível executar o aplicativo quando eles não estão conectados.  
  
 O `Install Mode` podem ser definidos na **Publish** página da **Designer de projeto**.  
  
 **Observação** o `Install Mode` também podem ser definidas usando o Assistente de publicação. Para obter mais informações, confira [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Para disponibilizar um aplicativo ClickOnce online apenas  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique o **publicar** guia.  
  
3. No **modo de instalação e as configurações** área, clique no **o aplicativo está disponível apenas online** botão de opção.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para disponibilizar um aplicativo ClickOnce online ou offline  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique o **publicar** guia.  
  
3. No **modo de instalação e as configurações** área, clique no **o aplicativo está disponível também offline** botão de opção.  
  
     Quando instalado, o aplicativo adiciona entradas para o **inicie** menu e, ao **adicionar ou remover programas** no painel de controle.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
