---
title: Caixa de diálogo Seletor de URL (desenvolvimento do SharePoint)
description: Saiba mais sobre a caixa de diálogo Seletor de URL, que permite que um usuário escolha arquivos localizados em seu projeto ou no servidor local que está executando o SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 584b77ab714cb692069fadd6c6fad50e20d46f80
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442528"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Caixa de diálogo Seletor de URL (desenvolvimento do SharePoint no Visual Studio)
  Na caixa de diálogo Seletor de URL, você pode escolher arquivos como arquivos de página mestra ou arquivos de imagem que estão localizados em seu projeto ou no servidor local que está executando o SharePoint.

 Essa caixa de diálogo aparece quando você tem a opção de escolher um arquivo para definir uma propriedade. Você pode abrir essa caixa de diálogo escolhendo o botão de reticências (![elipse do designer móvel ASP.net](../sharepoint/media/mwellipsis.gif "Elipse do designer móvel ASP.NET")) ao lado de várias propriedades na janela **Propriedades** . O botão de reticências também aparece como um prompt do IntelliSense quando você atribui valores a determinados atributos na exibição de **origem** do designer.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Pastas do projeto** Exibe uma lista das pastas definidas no projeto ou no servidor local que está executando o SharePoint. Escolha o botão de expansão para exibir as subpastas.

 Expanda o nó do **projeto** para escolher arquivos em seu projeto. Para aparecer como selecionável na caixa de diálogo, os arquivos em seu projeto devem atender aos seguintes critérios:

- O arquivo deve estar contido em uma pasta mapeada.

- O arquivo deve ser adicionado ao pacote de solução.

- O arquivo não pode estar localizado em outro projeto.

  Se desejar fazer referência a arquivos que não atendem a esses critérios, você precisará inserir o caminho do arquivo manualmente.

  Expanda o nó do **servidor** para escolher os arquivos que estão localizados no servidor local que está executando o SharePoint. Para aparecer como selecionável na caixa de diálogo, esses arquivos devem atender aos seguintes critérios:

- O arquivo deve estar localizado em uma das seguintes pastas mapeadas: **imagens**, **layouts** ou **ControlTemplates**.

- O arquivo não pode estar localizado no banco de dados de conteúdo do SharePoint.

  Se desejar fazer referência a arquivos que não atendem a esses critérios, você precisará inserir o caminho do arquivo manualmente.

  **Conteúdo da pasta** Exibe uma lista de arquivos na pasta selecionada. Escolha um arquivo e, em seguida, escolha o botão **OK** para fechar a caixa de diálogo e enviar sua seleção para o processo que a chamou.

  **Arquivos do tipo** Permite que você escolha em uma lista de arquivos que são apropriados para a tarefa que você está executando.

## <a name="see-also"></a>Confira também
- [Criar páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Criar Web Parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Criar controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
