---
title: 'Como: Especifique o local onde os usuários finais instalarão | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a148dd9f0f33805fcf0dae423f6a7e33a00ca22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989731"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Como: Especificar a localização da qual os usuários finais instalarão
Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, o local onde os usuários irão baixar e instalar o aplicativo não é necessariamente o local em que você publica o aplicativo inicialmente. Por exemplo, em algumas organizações, um desenvolvedor pode publicar um aplicativo em um servidor de preparo e, em seguida, um administrador seria mover o aplicativo para um servidor Web.  
  
 Nesse caso, você pode usar o `Installation URL` propriedade para especificar o servidor Web onde os usuários irão baixar o aplicativo. Isso é necessário para que o manifesto do aplicativo saiba onde procurar por atualizações.  
  
 O `Installation URL` propriedade pode ser definida na **Publish** página da **Designer de projeto**.  
  
 **Observação** as `Installation URL` propriedade também pode ser definida usando o **PublishWizard**. Para obter mais informações, confira [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Para especificar uma URL de instalação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No campo URL de instalação, insira o local de instalação usando uma URL totalmente qualificada usando o formato *http://www.microsoft.com/ApplicationName*, ou um caminho UNC usando o formato  *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Especificar onde o Visual Studio copiará os arquivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)