---
title: Opções, Editor de Texto, Todos os idiomas, Guias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662393"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opções, Editor de Texto, Todos os Idiomas, Guias
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta caixa de diálogo permite alterar o comportamento padrão do Editor de Código. Essas configurações também se aplicam a outros editores baseados no Editor de código, como o modo de exibição de Fonte do Designer de HTML. Para exibir essas opções, selecione **Opções** do menu **Ferramentas**. Na pasta **Editor de Texto**, expanda a subpasta **Todos os Idiomas** e, em seguida, escolha **Guias**.

> [!CAUTION]
> Esta página define opções padrão para todas as linguagens de desenvolvimento. Lembre-se de que redefinir uma opção nessa caixa de diálogo redefinirá as opções Guias em todas as linguagens para quaisquer opções selecionadas aqui. Para alterar as opções do Editor de Texto para apenas uma linguagem, expanda a subpasta para aquela linguagem e selecione suas páginas de opções.

 Se forem selecionadas configurações diferentes nas páginas de opções Guias para linguagens de programação específicas, a mensagem “As configurações de recuo para formatos de texto individuais estão em conflito entre si” será exibida para diferentes opções de **Recuo**, e a mensagem “As configurações de guia para formatos de texto individuais estão em conflito entre si” será exibida para diferentes opções de **Guia**. Por exemplo, esse lembrete será exibido se a opção **Recuo inteligente** for selecionada para Visual Basic, mas **Bloquear recuo** estiver selecionado para Visual C++.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="indenting"></a>Recuar
 Nenhum quando selecionado, novas linhas não são recuadas. O ponto de inserção é colocado na primeira coluna de uma linha nova.

 Bloquear quando selecionado, novas linhas serão recuadas automaticamente. O ponto de inserção é colocado no mesmo ponto de partida que a linha anterior.

 Quando a opção Smart é selecionada, novas linhas são posicionadas para caber no contexto do código, conforme as configurações de formatação do outro código e as convenções do IntelliSense para sua linguagem de desenvolvimento. Essa opção não está disponível para todas as linguagens de desenvolvimento.

 Por exemplo, as linhas incluídas entre uma chave de abertura ({) e uma chave de fechamento (}) podem ser recuadas automaticamente em uma parada de tabulação extra da posição das chaves alinhadas.

## <a name="tabs"></a>Tabulações
 Tamanho da Tabulação define a distância em espaços entre as paradas de tabulação. O padrão é quatro espaços.

 Tamanho do recuo define o tamanho em espaços de um recuo automático. O padrão é quatro espaços. Os caracteres de tabulação, os caracteres de espaço, ou ambos serão inseridos para preencher o tamanho especificado.

 Inserir espaços quando selecionado, as operações de recuo inserem apenas caracteres de espaço, não caracteres de TABULAção. Se o **Tamanho do recuo** estiver definido como 5, por exemplo, cinco caracteres de espaço serão inseridos sempre que você pressionar a tecla TAB ou o botão **Aumentar Recuo** na barra de ferramentas de **Formatação**.

 Manter guias quando selecionadas, as operações de recuo inserem o máximo possível de caracteres de guia. Cada caractere de TABULAÇÃO preenche o número de espaços especificado em **Tamanho da tabulação**. Se o **Tamanho do recuo** não for um múltiplo par do **Tamanho da tabulação**, os caracteres de espaço serão adicionados para preencher a diferença.

## <a name="see-also"></a>Veja também
 [Opções, editor de texto, todos os idiomas](../../ide/reference/options-text-editor-all-languages.md) [geral, caixa de diálogo opções de ambiente](../../ide/reference/general-environment-options-dialog-box.md)
