---
title: Definir a versão de publicação do ClickOnce | Microsoft Docs
description: Saiba como definir a propriedade versão de publicação do ClickOnce, que determina se o aplicativo é uma atualização.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885021"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Como definir a versão da publicação do ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propriedade determina se o aplicativo que você está publicando será tratado como uma atualização. Cada versão de tempo é incrementada, o aplicativo será publicado como uma atualização.

 A `Publish Version` propriedade pode ser definida na página **publicar** do designer de **projeto**.

> [!NOTE]
> Há uma opção de projeto que incrementará automaticamente a `Publish Version` Propriedade cada vez que o aplicativo for publicado; essa opção é habilitada por padrão. Para obter mais informações, consulte [como incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Para alterar a versão de publicação

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. Clique na guia **Publicar**.

3. No **campo versão de publicação** , aumente os números de versão **principal**, **secundária**, de **compilação** ou de **revisão** .

    > [!NOTE]
    > Você nunca deve decrementar um número de versão; Isso pode causar um comportamento de atualização imprevisível.

## <a name="see-also"></a>Confira também
- [Escolher uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Como: incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)