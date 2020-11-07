---
title: Alterar idioma de publicação para aplicativo ClickOnce
description: Saiba como especificar um idioma/cultura para um aplicativo localizar no ClickOnce, em vez de padronizar para o idioma/cultura do seu computador de desenvolvimento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fed8c137b5bce225d8a231bb5a263b87c2bf361
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350160"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Como alterar o idioma de publicação para um aplicativo ClickOnce

Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, a interface do usuário exibida durante a instalação usa como padrão o idioma e a cultura do seu computador de desenvolvimento. Se você estiver publicando um aplicativo localizado, será necessário especificar um idioma e uma cultura para corresponder à versão localizada. Isso é determinado pela `Publish language` Propriedade do seu projeto.

A `Publish language` propriedade pode ser definida na caixa de diálogo **Opções de publicação** , acessível na página **publicar** do **Designer de projeto**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, confira [Redefinir as configurações](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Para alterar a linguagem de publicação

1. Com um projeto selecionado no **Gerenciador de soluções** , no menu **projeto** , clique em **Propriedades**.

2. Clique na guia **Publicar**.

3. Clique no botão **Opções** para abrir a caixa de diálogo **Opções de publicação** .

4. Clique em **Descrição**.

5. Na caixa de diálogo **Opções de publicação** , selecione um idioma e uma cultura na lista suspensa **idioma de publicação** e clique em **OK**.

## <a name="see-also"></a>Veja também

- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)