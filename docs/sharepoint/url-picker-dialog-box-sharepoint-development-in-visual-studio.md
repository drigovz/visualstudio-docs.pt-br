---
title: Caixa de diálogo Seletor de URL (desenvolvimento do SharePoint no Visual Studio) | Microsoft Docs
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
ms.openlocfilehash: 8d8f193e50053b5cdf0b89cf41b09471c513ee9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007946"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Caixa de diálogo Seletor de URL (desenvolvimento do SharePoint no Visual Studio)
  Na caixa de diálogo Seletor de URL, você pode escolher arquivos como arquivos de página mestra ou arquivos de imagem que estão localizados em seu projeto ou no servidor local que está executando o SharePoint.

 Essa caixa de diálogo aparece quando você tem a opção de escolher um arquivo para definir uma propriedade. Você pode abrir essa caixa de diálogo escolhendo o botão de reticências (![elipse do Designer de dispositivo móvel do ASP.NET](../sharepoint/media/mwellipsis.gif "elipse do Designer de dispositivo móvel do ASP.NET")) ao lado de várias propriedades no **propriedades** janela. O botão de reticências também aparece como um IntelliSense prompt quando você atribui valores a determinados atributos na **origem** modo de exibição do designer.

## <a name="uielement-list"></a>Lista UIElement
 **Pastas de projeto** exibe uma lista de pastas definidas no projeto ou no servidor local que está executando o SharePoint. Escolha o botão de expansão para exibir subpastas.

 Expanda o **projeto** nó escolher arquivos em seu projeto. Para aparecer como selecionável na caixa de diálogo, arquivos em seu projeto devem atender aos seguintes critérios:

- O arquivo deve estar contido em uma pasta mapeada.

- O arquivo deve ser adicionado ao pacote de solução.

- O arquivo não pode ser localizado em outro projeto.

  Se você quiser fazer referência a arquivos que não atendem a esses critérios, você precisa digitar o caminho do arquivo manualmente.

  Expanda o **Server** nó escolher arquivos que estão localizados no servidor local que está executando o SharePoint. Para aparecer como selecionável na caixa de diálogo, esses arquivos devem atender aos seguintes critérios:

- O arquivo deve estar localizado em uma das seguintes pastas mapeadas: **Imagens**, **Layouts**, ou **ControlTemplates**.

- O arquivo não pode ser localizado no banco de dados de conteúdo do SharePoint.

  Se você quiser fazer referência a arquivos que não atendem a esses critérios, você precisa digitar o caminho do arquivo manualmente.

  **Conteúdo da pasta** exibe uma lista de arquivos na pasta selecionada. Escolha um arquivo e, em seguida, escolha o **Okey** botão para fechar a caixa de diálogo e enviar sua seleção para o processo que o chamou.

  **Arquivos do tipo** permite que você escolha dentre uma lista de arquivos que são apropriadas para a tarefa que você está executando.

## <a name="see-also"></a>Consulte também
- [Criar páginas de aplicativo do SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Criar web parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Criar controles reutilizáveis para web parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
