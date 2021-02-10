---
title: Incrementar automaticamente a versão de publicação do ClickOnce
description: Saiba como desabilitar o incremento automático de número de revisão para seu aplicativo ClickOnce usando o Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947769"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Como incrementar automaticamente a versão de publicação do ClickOnce

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, alterar a `Publish Version` propriedade faz com que o aplicativo seja publicado como uma atualização. Por padrão, o Visual Studio incrementa automaticamente o `Revision` número de `Publish Version` cada vez que você publica o aplicativo.

Você pode desabilitar esse comportamento na página **publicar** do designer de **projeto**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, confira [Redefinir as configurações](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para desabilitar o incrementamento automático da versão de publicação

1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.

2. Clique na guia **Publicar**.

3. Na seção **Publicar versão** , desmarque a caixa de seleção **incrementar revisão automaticamente com cada versão** .

## <a name="see-also"></a>Confira também

- [Como definir a versão da publicação do ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)