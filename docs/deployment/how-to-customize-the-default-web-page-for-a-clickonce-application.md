---
title: Personalizar página da Web padrão para o aplicativo ClickOnce
description: Saiba mais sobre a página da Web gerada quando você publica um aplicativo ClickOnce na Web, que contém o nome do aplicativo e outras informações.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0377bdc5fa38c814bb5cd6ff02d12dcec117266d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900790"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Como personalizar a página da Web padrão para um aplicativo ClickOnce
Ao publicar um aplicativo ClickOnce na Web, uma página da Web é gerada automaticamente e publicada junto com o aplicativo. A página padrão contém o nome do aplicativo e links para instalar o aplicativo, instalar pré-requisitos ou acessar a ajuda no MSDN.

> [!NOTE]
> Os links reais que você vê na página dependem do computador onde a página está sendo exibida e dos pré-requisitos que você está incluindo.

 O nome padrão da página da Web é *Publish.htm*; Você pode alterar o nome no **Designer de projeto**. Para obter mais informações, consulte [como: especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 A página da Web *Publish.htm* será publicada somente se uma versão mais recente for detectada.

> [!NOTE]
> As alterações feitas nas configurações de **publicação** não afetarão a página *Publish.htm* , com uma exceção: se você adicionar ou remover pré-requisitos após a publicação inicial, a lista de pré-requisitos não será mais precisa. Você precisará editar o texto para o link de pré-requisito para refletir as alterações.

### <a name="to-customize-the-publish-web-page"></a>Para personalizar a página de publicação da Web

1. Publique seu aplicativo ClickOnce em um local da Web. Para obter mais informações, consulte [como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. No servidor Web, abra o arquivo *Publish.htm* no Visual Web Designer ou em outro editor de HTML.

3. Personalize a página conforme desejado e salve-a.

4. Opcional. Para impedir que o Visual Studio substitua sua página da Web de publicação personalizada, desmarque a opção **gerar automaticamente implantação da Web após cada publicação** na caixa de diálogo **Opções de publicação** .

## <a name="see-also"></a>Confira também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como: instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Como especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)