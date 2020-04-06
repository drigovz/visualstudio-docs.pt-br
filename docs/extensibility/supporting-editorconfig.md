---
title: Estender o serviço de idiomas para dar suporte ao EditorConfig
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
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699580"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Suporte ao EditorConfig para o seu serviço de idiomas

Os arquivos [EditorConfig](https://editorconfig.org/) permitem descrever opções comuns de editor de texto, como tamanho de recuo, em uma base por projeto. Para saber mais sobre o suporte do Visual Studio aos arquivos EditorConfig, consulte [Criar configurações de editor portátil usando o EditorConfig](../ide/create-portable-custom-editor-options.md).

Na maioria dos casos, ao implementar um serviço de linguagem do Visual Studio, nenhum trabalho adicional é necessário para dar suporte às propriedades universais do EditorConfig. O editor básico detecta automaticamente e lê o arquivo .editorconfig quando os usuários abrem arquivos e define as opções de buffer e exibição de texto apropriadas. No entanto, para edições como guias e espaços, alguns serviços de idioma optam por usar uma opção de exibição de texto contextual apropriada em vez de usar configurações globais. Nesses casos, o serviço de linguagem deve ser atualizado para dar suporte aos arquivos do EditorConfig.

A seguir estão as alterações necessárias para atualizar um serviço de idioma para suportar arquivos do EditorConfig, substituindo uma opção _global específica de idioma_ por uma opção _contextual:_

## <a name="indent-style"></a>Estilo de recuo

Opções específicas do idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Tamanho do recuo

Opções específicas do idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tamanho da tabulação

Opções específicas do idioma | Opções contextuais
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Confira também

- [Crie configurações de editor portátil usando o EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Ampliando o editor e os serviços de idiomas](../extensibility/extending-the-editor-and-language-services.md)
