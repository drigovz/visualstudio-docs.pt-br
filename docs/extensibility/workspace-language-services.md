---
title: Espaços de trabalho e serviços de linguagem no Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952681"
---
# <a name="workspaces-and-language-services"></a>Espaços de trabalho e serviços de idioma

Os serviços de linguagem podem fornecer aos usuários de [pasta aberta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) os mesmos recursos de linguagem avançados aos quais eles são usados ao trabalhar com soluções e projetos. Um serviço de linguagem pode ser ativado automaticamente com base na extensão de arquivo ou no conteúdo de um documento aberto, embora esse serviço de linguagem "arquivo flexível" seja limitado ao realce de sintaxe. Informações adicionais são necessárias para fornecer uma experiência mais rica ao editar/revisar o código-fonte. Cada serviço de linguagem tem sua própria API para inicialização com esses dados contextuais adicionais para um documento. Normalmente, isso é gerenciado por um sistema de projeto, que é rigidamente acoplado ao serviço de linguagem e ao sistema de compilação.

## <a name="initialization"></a>Inicialização

Em um [espaço de trabalho](workspaces.md), os serviços de linguagem são inicializados por um <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> ponto de extensão especializado apenas nesse serviço de linguagem e não sabem nada da criação da compilação. Dessa forma, um proprietário de serviço de linguagem pode manter uma única extensão de pasta aberta, independentemente de quantos padrões existem em pastas e arquivos para executar o compilador durante uma compilação (por exemplo, MSBuild, makefiles, etc.). Quando os arquivos dos quais um contexto de arquivo foi criado são alterados no disco e o contexto do arquivo é atualizado, o provedor de serviços de idioma é notificado sobre o conjunto atualizado de contextos de arquivo. O provedor de serviços de linguagem pode então atualizar seu modelo.

Quando um documento é aberto no editor, o Visual Studio considera apenas os provedores de serviço de linguagem que exigem tipos de contexto de arquivo para os quais um provedor de contexto de arquivo correspondente pode ser encontrado. Em seguida, ele passa os contexto de arquivo do (s) provedor (es) correspondente para o provedor de serviços de idioma selecionado via `ILanguageServiceProvider.InitializeAsync` . O que o provedor de serviços de linguagem faz com esses dados de contexto de arquivo é um detalhe de implementação do provedor de serviços de idioma, mas a experiência do usuário esperada é um serviço de linguagem mais rico para esse documento aberto.

## <a name="using-ilanguageserviceprovider"></a>Usando ILanguageServiceProvider

O serviço de idioma será notificado quando um contexto de arquivo for criado com um `ContextType` que corresponda a um dos `SupportedContextTypes` valores do atributo de exportação do servidor de idioma.

Para dar suporte a um serviço de idioma, uma extensão precisará de:

- Um exclusivo `Guid` . Isso será usado para `SupportedContextTypes` argumentos de atributo e em um `FileContext` objeto.
- Contexto do arquivo de idioma
  - Fábrica de provedores
    - `ExportFileContextProviderAttribute` atributo com o acima gerado exclusivamente `Guid` em `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementação de provedor de `IFileContextProvider.GetContextsForFileAsync`
    - Construir um novo `FileContext` com o `contextType` argumento do Construtor como o gerado exclusivamente `Guid`
    - Use a `Context` Propriedade do `FileContext` para fornecer dados adicionais ao `ILanguageServiceProvider`
- Serviço de linguagem
  - Fábrica de provedores
    - `ExportLanguageServiceProvider` atributo com o acima gerado exclusivamente `Guid` em `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Provedor
    - Implementa `ILanguageServiceProvider`
    - Usar `ILanguageServiceProvider.InitializeAsync` para habilitar serviços de linguagem para os argumentos fornecidos quando um arquivo é aberto
    - Use `ILanguageServiceProvider.UninitializeAsync` para desabilitar os serviços de linguagem para os argumentos fornecidos quando um arquivo é fechado

>[!WARNING]
>Os `ILanguageServiceProvider` métodos podem ser invocados pelo espaço de trabalho no thread principal. Considere o agendamento do trabalho em um thread diferente para evitar a introdução de atrasos da interface do usuário.

## <a name="language-server-protocol"></a>Language Server Protocol

As `Microsoft.VisualStudio.Workspace.*` APIs não são a única maneira de habilitar o serviço de idioma na pasta aberta. Outra opção é usar um servidor de idioma. Para obter mais informações, leia sobre o [protocolo de servidor de linguagem](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> é invocado quando um arquivo de tipos de arquivo correspondentes é aberto ou fechado para edição.

## <a name="next-steps"></a>Próximas etapas

* [Build do espaço de trabalho](workspace-build.md) – abrir pasta dá suporte a sistemas de compilação, como MSBuild e makefiles.