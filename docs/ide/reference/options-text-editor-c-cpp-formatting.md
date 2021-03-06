---
title: Opções, Editor de Texto, C/C++, Formatação
description: Saiba como usar a página opções de formatação e suas subpáginas para definir opções de formatação de código no editor de código quando você estiver programando em C e C++.
ms.custom: SEO-VS-2020
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 264485fd8f20ee31046035dba7b208795d0d91b0
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041081"
---
# <a name="options-text-editor-cc-formatting"></a>Opções, Editor de Texto, C/C++, Formatação

Use essas páginas de propriedades para alterar o comportamento padrão do editor de código ao programar em C ou C++.

![Páginas de propriedades de Formatação do C++](media/cpp-formatting.png)

Para acessar essa página, na caixa de diálogo **Opções**, no painel esquerdo, expanda **Editor de Texto**, expanda **C/C++** e clique em **Formatação**.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Página Geral

Esta página contém as opções de formatação de instruções e de blocos conforme você os digita.

::: moniker range="vs-2017"

**Visual Studio 2017 versão 15,7 e posterior**:

::: moniker-end

A página também tem opções para configurar o suporte para o [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) versão 5.0. O ClangFormat é um utilitário que facilita a definição do estilo e a formatação do código com base em um conjunto de regras que pode ser configurado em um arquivo .clang-format ou _clang-format.

### <a name="configuring-clangformat-options"></a>Configurando as opções de ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 versão 15,7 e posterior**:

::: moniker-end

O suporte a ClangFormat está habilitado por padrão. Você pode escolher quais dessas convenções de formatação comuns serão aplicadas a todos os seus projetos: LLVM, Google, Chromium, Mozilla ou WebKit. Você também pode criar um arquivo .clang-format ou _clang-format de definição de formato personalizado. Quando esse arquivo está presente em uma pasta de projeto, o Visual Studio o usa para formatar todos os arquivos de código-fonte nessa pasta e em suas subpastas.

Por padrão, o Visual Studio executa o clangformat.exe em segundo plano e aplica a formatação à medida que você digita. Você também pode especificar que ele seja executado somente para comandos de formatação invocados manualmente **Formatar Documento (Ctrl + K, Ctrl + D)** ou **Formatar Seleção (Ctrl + K, Ctrl + F)**.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Páginas de Recuo, Novas Linhas, Disposição de Espaçamento

Essas páginas habilitam várias personalizações de formatação, mas que são ignoradas quando ClangFormat está habilitado.

## <a name="see-also"></a>Confira também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Usando o IntelliSense](../../ide/using-intellisense.md)
