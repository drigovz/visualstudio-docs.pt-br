---
title: Opções, Editor de Texto, Todos os idiomas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662397"
---
# <a name="options-text-editor-all-languages"></a>Opções, Editor de Texto, Todos os Idiomas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta caixa de diálogo permite alterar o comportamento padrão do Editor de Código. Essas configurações também se aplicam a outros editores baseados no Editor de código, como o modo de exibição de Fonte do Designer de HTML. Para abrir essa caixa de diálogo, selecione **Opções** no menu **Ferramentas**. Dentro da pasta **Editor de Texto**, expanda a subpasta **Todos os Idiomas** e, em seguida, escolha **Geral**.

> [!CAUTION]
> Esta página define opções padrão para todas as linguagens de desenvolvimento. Lembre-se de que redefinir uma opção nessa caixa de diálogo redefinirá as opções Geral em todas as linguagens, não importa quais opções sejam selecionadas aqui. Para alterar as opções do Editor de Texto para apenas uma linguagem, expanda a subpasta para aquela linguagem e selecione suas páginas de opções.

 Uma marca de seleção esmaecida é exibida quando uma opção tiver sido selecionada nas páginas de opções Geral para algumas linguagens de programação, mas não para outras.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Conclusão de instrução
 Listar Membros automaticamente quando selecionada, listas pop-up de membros, propriedades, valores ou métodos disponíveis são exibidos pelo IntelliSense conforme você digita no editor. Escolha qualquer item na lista pop-up para inserir o item em seu código. Selecionar essa opção habilita a opção **Ocultar membros avançados**.

 Ocultar membros avançados quando selecionado, reduz as listas de preenchimento de instrução pop-up exibindo somente os itens mais usados. Os outros itens são filtrados da lista.

 Informações de parâmetro quando selecionado, a sintaxe completa para a declaração ou procedimento atual é exibida sob o ponto de inserção no editor, com todos os seus parâmetros disponíveis. O próximo parâmetro que você pode atribuir é exibido em negrito.

## <a name="settings"></a>Configurações
 Habilitar espaço virtual quando essa opção é selecionada e a **quebra automática** de linha é desmarcada, você pode clicar em qualquer lugar além do final de uma linhas no editor de código e digitar. Esse recurso pode ser usado para posicionar comentários em um ponto consistente ao lado do seu código.

 Quebra automática de linha quando selecionada, qualquer parte de uma linhas que se estenda horizontalmente além da área do editor visível será exibida automaticamente na próxima linha. Selecionar essa opção habilita a opção **Mostrar glifos visuais para quebra automática de linha**.

> [!NOTE]
> O recurso **Espaço Virtual** é desativado enquanto **Quebra automática de linha** está ativada.

 Mostrar glifos visuais para quebra automática de linha quando selecionado, um indicador de seta de retorno é exibido em que uma longa quebra é decodificada em uma segunda linha.

 ![Captura de tela de LineBreakSymbol](../../ide/reference/media/linebreak.gif "linebreak")

 Desmarque esta opção se preferir não exibir esses indicadores.

> [!NOTE]
> Essas setas de lembrete não são adicionadas ao seu código, e não imprimem. Eles são somente para referência.

 Aplicar comandos Recortar ou copiar a linhas em branco quando não houver seleção essa opção define o comportamento do editor quando você coloca o ponto de inserção em uma linha em branco, não seleciona nada e, em seguida, copia ou recorta.

- Quando essa opção está selecionada, a linha em branco é copiada ou cortada. Se você então Colar, uma nova linha em branco será inserida.

- Quando essa opção está desmarcada, o comando Cortar remove linhas em branco. No entanto, os dados na Área de Transferência são preservados. Portanto, se você usar o comando Colar, o conteúdo copiado mais recentemente para a Área de Transferência será colado. Se nada foi copiado anteriormente, nada será colado.

  Essa configuração não tem efeito sobre o Copiar ou Cortar quando uma linha não está em branco. Se nada for selecionado, a linha inteira será copiada ou recortada. Se você então Colar, o texto da linha inteira e seu caractere de fim de linha serão colados.

> [!TIP]
> Para exibir indicadores para espaços, tabulações e fins de linha, e assim distinguir linhas recuadas de linhas totalmente em branco, selecione **Avançado** no menu **Editar** e escolha **Exibir Espaço em Branco**.

## <a name="display"></a>Monitor
 Números de linha quando selecionado, um número de linha é exibido ao lado de cada linha de código.

> [!NOTE]
> Esses números de linha não são adicionados ao seu código e não são impressos. Eles são somente para referência.

 Habilitar navegação de URL de clique único quando selecionado, o cursor do mouse muda para uma mão apontando para uma URL no editor. Você pode clicar no URL para exibir a página indicada em seu navegador da Web.

 Barra de navegação quando selecionada, exibe a **barra de navegação** na parte superior do editor de código. Suas listas suspensas **Objetos** e **Membros** permitem escolher um objeto específico no código, selecionar entre seus membros e navegar para a declaração do membro selecionado no Editor de Códigos.

## <a name="see-also"></a>Consulte Também
 [Opções, editor de texto, todas as linguagens, guias](../../ide/reference/options-text-editor-all-languages-tabs.md) [geral, ambiente, caixa de diálogo opções](../../ide/reference/general-environment-options-dialog-box.md) [usando o IntelliSense](../../ide/using-intellisense.md)
