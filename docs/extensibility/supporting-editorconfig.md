---
title: Estender o serviço de linguagem para dar suporte a EditorConfig
description: Saiba mais sobre as alterações a serem feitas para atualizar um serviço de idioma para dar suporte a arquivos EditorConfig. Substitua uma opção global específica da linguagem por uma opção contextual.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c635df2301822fc1bb982df44912527d53c9ef6
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716101"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Suporte a EditorConfig para seu serviço de idioma

Os arquivos [EditorConfig](https://editorconfig.org/) permitem que você descreva as opções comuns do editor de texto, como tamanho do recuo, em uma base por projeto. Para saber mais sobre o suporte do Visual Studio para arquivos EditorConfig, consulte [criar configurações de editor portátil usando o EditorConfig](../ide/create-portable-custom-editor-options.md).

Na maioria dos casos, ao implementar um serviço de linguagem do Visual Studio, nenhum trabalho adicional é necessário para dar suporte às propriedades universais do EditorConfig. O editor básico detecta automaticamente e lê o arquivo .editorconfig quando os usuários abrem arquivos e define as opções de buffer e exibição de texto apropriadas. No entanto, para edições como tabulares e espaços, alguns serviços de idioma optam por usar uma opção de exibição de texto contextual apropriada em vez de usar configurações globais. Nesses casos, o serviço de linguagem deve ser atualizado para dar suporte aos arquivos do EditorConfig.

Veja a seguir as alterações necessárias para atualizar um serviço de idioma para dar suporte a arquivos EditorConfig, substituindo uma opção global _específica da linguagem_ por uma opção _contextual_ :

## <a name="indent-style"></a>Estilo de recuo

Opções específicas de idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Tamanho do recuo

Opções específicas de idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tamanho da tabulação

Opções específicas de idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Consulte também

- [Criar configurações de editor portátil usando EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Estendendo o editor e os serviços de linguagem](../extensibility/extending-the-editor-and-language-services.md)
