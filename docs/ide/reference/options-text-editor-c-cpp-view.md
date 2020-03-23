---
title: Opções, Editor de Texto, C/C++, Exibição
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 95963245b15828f374e9812a9bb09d015b21a94b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278685"
---
# <a name="options-text-editor-cc-view"></a>Opções, Editor de Texto, C/C++, Exibição

Use essas páginas de propriedades para alterar o comportamento padrão do editor de código ao programar em C ou C++.

Para acessar esta página de propriedade, escolha **Opções de** > **ferramentas** e expanda o Editor de **texto,** depois **C/C++** e, em seguida, escolha **Exibir**.

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

## <a name="see-also"></a>Confira também

- [Definindo opções de editor específicos do idioma](../../ide/reference/setting-language-specific-editor-options.md)
- [Refatoração em C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
