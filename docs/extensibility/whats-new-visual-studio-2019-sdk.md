---
title: Novidades no Visual Studio 2019 SDK | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740404"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novidades do SDK do Visual Studio 2019

O Visual Studio SDK tem os seguintes recursos novos e atualizados para o Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Aviso de extensões carregadas de forma sincronizada auto-carregada

Os usuários agora verão um aviso se alguma de suas extensões instaladas for carregada sincronicamente na inicialização. Você pode aprender mais sobre o aviso em [extensões síncronicamente carregadas automaticamente](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Único, unificado Visual Studio SDK

Agora você pode obter todos os ativos Do Visual Studio SDK através de um único pacote NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Aprimoramentos de registro de editores

Desde a sua criação, o Visual Studio tem suportado o registro personalizado do editor onde um editor pode declarar sua afinidade por extensões específicas (por exemplo, .xaml e .rc), ou que é adequado para qualquer extensão (.*). A partir do Visual Studio 2019 versão 16.1, ampliamos o suporte para registro de editor.

### <a name="filenames"></a>Nomes de arquivos

Além de registrar o suporte para uma determinada extensão de arquivo, um editor pode registrar que `ProvideEditorFilename` ele suporta nomes de arquivos específicos aplicando o novo atributo ao pacote do editor.

Por exemplo, um editor que suporta todos os `ProvideEditorExtension` arquivos .json aplicaria esse atributo ao seu pacote:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partir do 16.1, se o MyEditor só suportar alguns arquivos .json bem conhecidos, ele pode, em vez disso, aplicar esses `ProvideEditorFilename` atributos ao seu pacote:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Um editor pode registrar um ou mais UIContexts que representam quando ele está ativado. UIContexts são registrados aplicando uma ou `ProvideEditorUIContextAttribute` mais instâncias do pacote que registra o editor.

Se um editor tiver registrado UIContexts:

- Se pelo menos um de seus UIContexts registrados estiver ativo quando um arquivo com a extensão dada for aberto, o editor será incluído na pesquisa do editor.
- Se nenhum dos UIContexts registrados estiver ativo, o editor não será incluído na pesquisa do editor.

Se um editor não registrar nenhum UIContexts, ele está sempre incluído na pesquisa do editor por essa extensão.

Por exemplo, se um editor estiver disponível apenas quando um projeto C# `ProvideEditorUIContext` estiver aberto, ele poderá declarar essa afinidade aplicando um atributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
