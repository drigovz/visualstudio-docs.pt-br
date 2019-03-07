---
title: 'Como: personalizar a página da Web padrão para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9831c1176b5e71650742226e77bfca58dfa35a01
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608430"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Como personalizar a página da Web padrão para um aplicativo ClickOnce
Ao publicar um aplicativo ClickOnce para a Web, uma página da Web é gerada automaticamente e publicada com o aplicativo. A página padrão contém o nome do aplicativo e links para instalar o aplicativo, instale os pré-requisitos ou acessar a Ajuda no MSDN.

> [!NOTE]
>  Os links reais que você vê na página dependem do computador em que a página estiver sendo exibida e o que você está incluindo de pré-requisitos.

 É o nome padrão para a página da Web *Publish. htm*; você pode alterar o nome na **Designer de projeto**. Para obter mais informações, consulte [como: especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 O *Publish. htm* página da Web é publicada somente se for detectada uma versão mais recente.

> [!NOTE]
>  As alterações feitas ao seu **publicar** configurações não afetarão o *Publish. htm* página, com uma exceção: se você adicionar ou remove os pré-requisitos depois de publicar inicialmente, a lista de pré-requisitos será não sejam mais precisos. Você precisará editar o texto do link de pré-requisito refletir as alterações.

### <a name="to-customize-the-publish-web-page"></a>Para personalizar a página Web publicar

1.  Publica seu aplicativo ClickOnce em um local da Web. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2.  No servidor Web, abra o *Publish. htm* arquivo no Visual Web Designer ou outro editor de HTML.

3.  Personalizar a página conforme desejado e salve-o.

4.  Opcional. Para impedir que o Visual Studio substituindo sua página da Web de publicação personalizadas, desmarque a opção **gerar automaticamente a página da Web de implantação após cada publicação** no **opções de publicação** caixa de diálogo.

## <a name="see-also"></a>Consulte também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Como especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)