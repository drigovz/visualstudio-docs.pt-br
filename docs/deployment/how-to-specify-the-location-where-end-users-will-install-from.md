---
title: Especifique o local para onde os usuários finais são instalados
description: Saiba como definir a propriedade URL de instalação, que é onde um aplicativo ClickOnce publicado é hospedado para instalação.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3518a2eef331414e5c73c0cebb36681ad2b72d61
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349614"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Como especificar o local de onde os usuários finais instalarão

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, o local onde os usuários acessam baixar e instalar o aplicativo não é necessariamente o local onde você publicará o aplicativo inicialmente. Por exemplo, em algumas organizações, um desenvolvedor pode publicar um aplicativo em um servidor de preparo e, em seguida, um administrador moveria o aplicativo para um servidor Web.

Nesse caso, você pode usar a `Installation URL` propriedade para especificar o servidor Web onde os usuários vão baixar o aplicativo. Isso é necessário para que o manifesto do aplicativo saiba onde procurar atualizações.

A `Installation URL` propriedade pode ser definida na página **publicar** do designer de **projeto**.

> [!NOTE]
> A `Installation URL` propriedade também pode ser definida usando o **PublishWizard**. Para obter mais informações, consulte [como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Para especificar uma URL de instalação

1. Com um projeto selecionado no **Gerenciador de soluções** , no menu **projeto** , clique em **Propriedades**.

2. Clique na guia **Publicar**.

3. No campo URL de instalação, insira o local de instalação usando uma URL totalmente qualificada usando o formato `https://www.contoso.com/ApplicationName` ou um caminho UNC usando o formato `\Server\ApplicationName` .

## <a name="see-also"></a>Veja também
- [Como especificar para onde o Visual Studio copia os arquivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)