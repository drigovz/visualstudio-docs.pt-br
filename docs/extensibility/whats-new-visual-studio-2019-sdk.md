---
title: O que há de novo no SDK do Visual Studio 2019 | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f818d89a51603bf2698e6c1db034f5341f23098
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086553"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novidades do SDK do Visual Studio 2019

O SDK do Visual Studio tem os seguintes recursos novos e atualizados para o Visual Studio de 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Forma síncrona extensões carregado automaticamente de aviso

Agora os usuários verão um aviso se qualquer uma das suas extensões instaladas sincronicamente são carregados automaticamente na inicialização. Você pode aprender mais sobre o aviso no [sincronicamente carregado automaticamente extensões](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Único e unificado SDK do Visual Studio

Agora você pode obter todos os ativos do SDK do Visual Studio por meio de um único pacote NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Aprimoramentos de registro de editor

Desde sua criação, Visual Studio tem suporte para registro de editor personalizado em que um editor pode declarar sua afinidade para extensões específicas (por exemplo,. XAML e. rc) ou que ele é adequado para qualquer extensão (. *). A partir do Visual Studio 2019 versão 16.1, podemos ampliar o suporte para o editor de registro.

### <a name="filenames"></a>Nomes de arquivos

Além ou em vez de, registrando o suporte para uma extensão de arquivo específico, um editor pode registrar que ele dá suporte a nomes de arquivos específicos ao aplicar o novo `ProvideEditorFilename` ao pacote do editor de atributo.

Por exemplo, um editor que dá suporte a todos os arquivos. JSON aplicaria isso `ProvideEditorExtension` de atributo para o seu pacote:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Começando com 16.1, se MyEditor só dá suporte a dois arquivos. JSON bem conhecido, ele pode em vez disso, aplicá-las `ProvideEditorFilename` atributos ao seu pacote:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Um editor pode registrar um ou mais UIContexts que representam quando ele é habilitado. UIContexts são registrados por meio da aplicação de uma ou mais instâncias de `ProvideEditorUIContextAttribute` ao pacote que registra o editor.

Se um editor tem UIContexts registrados:

- Se pelo menos um dos seus UIContexts registrado estiver ativo quando um arquivo com a extensão fornecida é aberto, o editor está incluído na pesquisa do editor.
- Se nenhum do UIContexts registrado estiver ativo, o editor não está incluído na pesquisa do editor.

Se um editor não registra quaisquer UIContexts, ele é sempre incluído na pesquisa de editor para essa extensão.

Por exemplo, se um editor está disponível apenas quando um C# projeto estiver aberto, ele pode declarar este afinidade aplicando uma `ProvideEditorUIContext` atributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```