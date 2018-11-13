---
title: Opções, Editor de Texto, C/C++, Exibição
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf1cde04a45df47627b8b8bf9a0fad7b9bef0c4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673193"
---
# <a name="options-text-editor-cc-view"></a>Opções, Editor de Texto, C/C++, Exibição

Use essas páginas de propriedades para alterar o comportamento padrão do editor de código ao programar em C ou C++.

Para acessar essa página de propriedades, escolha **Ferramentas** > **Opções** e expanda **Editor de Texto** e **C/C++** e, em seguida, escolha **Exibir**.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="code-squiggles"></a>Linhas ondulantes de código

É possível habilitar ou desabilitar as seguintes configurações para gerenciar a maneira como o editor de texto trata as linhas ondulantes de código para C e C++:

- **Macros em regiões de navegação ignorada** – define como realçar macros que estão dentro de regiões ignoradas no banco de dados de navegação, como as macros cujas definições incluem chaves.

- **Macros conversíveis em constexpr** – define como realçar definições de macro que podem ser convertidas em definições do `constexpr`.

## <a name="inactive-code"></a>Código inativo

- **Mostrar blocos inativos** – os blocos inativos do pré-processador são coloridos de maneira diferente.

- **Desabilitar opacidade de cor inativa** – uma cor sólida, em vez de opacidade, é usada para blocos de códigos inativos.

- **Percentual de opacidade de código inativo** – o percentual de opacidade para blocos de códigos inativos.

## <a name="miscellaneous"></a>Diversos

- **Enumerar tarefas de comentário** – Examinar arquivos de software livre para tokens do VS e relate-os na janela Lista de Tarefas.

- **Realçar tokens correspondentes** – Realçar chaves de fechamento ou a sintaxe que corresponde ao local em que o cursor está posicionado. 

## <a name="outlining"></a>Estrutura de tópicos

- **Habilitar estrutura de tópicos** – Entrar no modo de estrutura de tópicos quando um arquivo é aberto.

- **Estruturar Regiões Pragma** – Estruturar automaticamente blocos de regiões `#pragma`.

- **Estruturar Blocos de Instrução** – Estruturar automaticamente blocos de instrução.

## <a name="see-also"></a>Consulte também

- [Configurando opções do editor específicas a um idioma](../../ide/reference/setting-language-specific-editor-options.md)
- [Refatoração em C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
