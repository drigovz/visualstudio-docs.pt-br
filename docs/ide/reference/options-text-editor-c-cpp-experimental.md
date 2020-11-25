---
title: Opções, Editor de Texto, C/C++, Experimental
description: Saiba como usar a página experimental na seção C/C++ para alterar os comportamentos experimentais relacionados ao IntelliSense e ao banco de dados de navegação.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: e35bdb8c6a56ef3174277836769201cd00e47dad
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040297"
---
# <a name="options-text-editor-cc-experimental"></a>Opções, Editor de Texto, C/C++, Experimental

Ao alterar essas opções, você pode alterar o comportamento relacionado ao IntelliSense e ao banco de dados de navegação quando estiver programando em C ou C++. Essas funcionalidades são realmente experimentais e podem ser modificadas ou removidas do Visual Studio em uma versão futura.

::: moniker range="vs-2017"

Este artigo descreve as opções no Visual Studio 2017. Para o Visual Studio 2015, selecione **2015** no seletor acima do sumário.

::: moniker-end

Para acessar essa página de propriedades, pressione **Ctrl** + **Q** para ativar a caixa de pesquisa e, em seguida, digite **experimental**. A Pesquisa encontra a página após as primeiras letras. Você também pode acessá-lo escolhendo **ferramentas**  >  **Opções** e expandindo o **Editor de texto**, em seguida, **C/C++** e escolhendo **experimental**.

Essas funcionalidades estão disponíveis em uma instalação do Visual Studio.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Habilitar IntelliSense Preditivo

O IntelliSense Preditivo limita o número de resultados exibidos na lista suspensa do IntelliSense para que você veja apenas os resultados relevantes no contexto. Por exemplo, se você digitar `int x =` e invocar a lista suspensa do IntelliSense, verá apenas inteiros ou funções que retornam inteiros. O IntelliSense Preditivo está desativado por padrão.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Habilitar carregamento de projeto mais rápido

No Visual Studio 2017 versão 15.3 em diante, essa funcionalidade é chamada **Habilitar Cache de Projeto** e foi movida para a página de propriedades [Configurações de Projeto do VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).

Essa opção permite que o Visual Studio coloque em cache os dados de projeto, para quando você abrir o projeto na próxima vez, ele pode carregar esses dados armazenados em cache em vez de recalcular dos arquivos de projeto. Usar dados armazenados em cache pode acelerar significativamente o tempo de carregamento do projeto.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Recursos adicionais no Visual Studio Marketplace

Você pode procurar outros recursos do editor de texto no [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Um exemplo é [C++ Quick Fixes](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017) (Correções Rápidas C++), que dá suporte ao seguinte:

- **Add missing #include (Adicionar #include ausente)** –sugere #include relevantes para símbolos desconhecidos no seu código

- **Add using namespace/Fully qualify symbol (Adicionar usando namespace/símbolo totalmente qualificado)** – semelhante ao item anterior, mas para namespaces

- **Add missing semicolon (adicionar ponto e vírgula ausente)**

- **Ajuda online** – pesquise mensagens de erro na ajuda online

- E muito mais…

## <a name="see-also"></a>Confira também

- [Definindo opções do editor de Language-Specific](../../ide/reference/setting-language-specific-editor-options.md)
- [Refatoração em C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
