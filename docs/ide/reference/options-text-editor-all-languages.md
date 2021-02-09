---
title: Opções, Editor de Texto, Todos os Idiomas
description: Saiba como usar a página Geral na seção todos os idiomas para alterar o comportamento padrão do editor de código no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b507f79aa4afb1bd5d2f56893d2e32aae0db4c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905568"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Caixa de diálogo opções: editor de texto \> todos os idiomas

Esta caixa de diálogo permite alterar o comportamento padrão do Editor de Código. Essas configurações também se aplicam a outros editores baseados no Editor de código, como o modo de exibição de Fonte do Designer de HTML. Para abrir essa caixa de diálogo, selecione **Opções** no menu **Ferramentas**. Dentro da pasta **Editor de Texto**, expanda a subpasta **Todos os Idiomas** e, em seguida, escolha **Geral**.

> [!CAUTION]
> Esta página define opções padrão para todas as linguagens de desenvolvimento. Lembre-se de que redefinir uma opção nessa caixa de diálogo redefinirá as opções Geral em todas as linguagens, não importa quais opções sejam selecionadas aqui. Para alterar as opções do Editor de Texto para apenas uma linguagem, expanda a subpasta para aquela linguagem e selecione suas páginas de opções.

Uma marca de seleção esmaecida é exibida quando uma opção tiver sido selecionada nas páginas de opções Geral para algumas linguagens de programação, mas não para outras.

## <a name="statement-completion"></a>Conclusão de instrução

**Listar membros automaticamente**

Quando selecionadas, listas pop-up de membros, propriedades, valores ou métodos disponíveis são exibidas pelo IntelliSense conforme você digita no editor. Escolha qualquer item na lista pop-up para inserir o item em seu código. Selecionar essa opção habilita a opção **Ocultar membros avançados**.

**Ocultar membros avançados**

Quando selecionada, diminui listas de preenchimento de declaração pop-up exibindo somente os itens mais usados. Os outros itens são filtrados da lista.

**Informações sobre parâmetros**

Quando selecionada, a sintaxe completa para a declaração ou procedimento atual é exibida sob o ponto de inserção no editor, com todos os seus parâmetros disponíveis. O próximo parâmetro que você pode atribuir é exibido em negrito.

## <a name="settings"></a>Settings

**Habilitar espaço virtual**

Quando esta opção está selecionada e a caixa de seleção **Quebra automática de linha** está desmarcada, você pode clicar em qualquer lugar além do final de uma linha no Editor de Códigos e digitar. Esse recurso pode ser usado para posicionar comentários em um ponto consistente ao lado do seu código.

**Quebra automática de linha**

Quando selecionada, qualquer parte de uma linha que se estenda horizontalmente além da área visível do editor é exibida automaticamente na próxima linha. Selecionar essa opção habilita a opção **Mostrar glifos visuais para quebra automática de linha**.

> [!NOTE]
> O recurso **Espaço Virtual** é desativado enquanto **Quebra automática de linha** está ativada.

**Mostrar glifos visuais para quebra automática de linha**

Quando selecionada, um indicador de seta d retorno é exibido no ponto em que uma linha longa quebra-se para uma segunda linha.

![Captura de tela de LineBreakSymbol](../../ide/reference/media/linebreak.gif)

Desmarque esta opção se preferir não exibir esses indicadores.

> [!NOTE]
> Essas setas de lembrete não são adicionadas ao seu código, e não imprimem. Eles são somente para referência.

**Números de linha**

Quando selecionada, um número de linha aparece ao lado de cada linha de código.

> [!NOTE]
> Esses números de linha não são adicionados ao seu código e não são impressos. Eles são somente para referência.

**Habilitar navegação de URL com um só clique**

Quando selecionada, o cursor do mouse muda para uma mão apontando conforme passa sobre uma URL no editor. Você pode clicar no URL para exibir a página indicada no seu navegador da Web.

**Barra de navegação**

Quando selecionada, exibe a **Barra de navegação** na parte superior do editor de código. Suas listas suspensas **Objetos** e **Membros** permitem escolher um objeto específico no código, selecionar entre seus membros e navegar para a declaração do membro selecionado no Editor de Códigos.

**Aplicar comandos Recortar ou Copiar a linhas em branco quando não houver nenhuma seleção**

Esta opção define o comportamento do editor quando você coloque o ponto de inserção em uma linha em branco, não seleciona nada e então Copia ou Corta.

- Quando essa opção está selecionada, a linha em branco é copiada ou cortada. Se você então Colar, uma nova linha em branco será inserida.

- Quando essa opção está desmarcada, o comando Cortar remove linhas em branco. No entanto, os dados na Área de Transferência são preservados. Portanto, se você usar o comando Colar, o conteúdo copiado mais recentemente para a Área de Transferência será colado. Se nada foi copiado anteriormente, nada será colado.

Essa configuração não tem efeito sobre o Copiar ou Cortar quando uma linha não está em branco. Se nada for selecionado, a linha inteira será copiada ou recortada. Se você então Colar, o texto da linha inteira e seu caractere de fim de linha serão colados.

> [!TIP]
> Para exibir indicadores para espaços, tabulações e fins de linha, e assim distinguir linhas recuadas de linhas totalmente em branco, selecione **Avançado** no menu **Editar** e escolha **Exibir Espaço em Branco**.

## <a name="see-also"></a>Confira também

- [Opções, Editor de Texto, Todas as Linguagens, Guias](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Usando o IntelliSense](../../ide/using-intellisense.md)
