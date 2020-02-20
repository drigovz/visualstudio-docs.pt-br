---
title: Como especificar o local para onde os usuários finais serão instalados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 794d417d3995e35b48dc6102bfdeddfa8b992548
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476901"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Como especificar o local de onde os usuários finais instalarão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao publicar um aplicativo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], o local em que os usuários acessam baixar e instalar o aplicativo não é necessariamente o local onde você publicará o aplicativo inicialmente. Por exemplo, em algumas organizações, um desenvolvedor pode publicar um aplicativo em um servidor de preparo e, em seguida, um administrador moveria o aplicativo para um servidor Web.  
  
 Nesse caso, você pode usar a propriedade `Installation URL` para especificar o servidor Web onde os usuários vão baixar o aplicativo. Isso é necessário para que o manifesto do aplicativo saiba onde procurar atualizações.  
  
 A propriedade `Installation URL` pode ser definida na página **publicar** do designer de **projeto**.  
  
 **Observação** A propriedade `Installation URL` também pode ser definida usando o **PublishWizard**. Para obter mais informações, consulte [como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Para especificar uma URL de instalação  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique na guia **Publicar**.  
  
3. No campo URL de instalação, insira o local de instalação usando uma URL totalmente qualificada usando o formato https://www.microsoft.com/ApplicationNameou um caminho UNC usando o formato \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Consulte Também  
 [Como especificar o local em que o Visual Studio copiará os arquivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
