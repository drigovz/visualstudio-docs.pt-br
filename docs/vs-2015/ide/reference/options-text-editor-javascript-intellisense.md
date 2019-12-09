---
title: Opções, Editor de Texto, JavaScript, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662227"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opções, Editor de Texto, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a página **IntelliSense** da caixa de diálogo **Opções** para modificar as configurações que afetam o comportamento do IntelliSense para JavaScript. É possível acessar a página **IntelliSense** escolhendo **Ferramentas**, **Opções** na barra de menus e expandindo **Editor de Texto**, **JavaScript**, **IntelliSense.**

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 A página **IntelliSense** contém as seguintes seções:

## <a name="validation"></a>Validação
 Você pode usar essas opções para definir preferências de como o editor JavaScript valida a sintaxe no seu documento.

## <a name="uielement-list"></a>Lista UIElement
 **Mostrar erros de sintaxe** Quando essa caixa de seleção não está marcada, o editor de código JavaScript não mostra erros de sintaxe. Isso será útil se você estiver trabalhando com código que não escreveu e não pretende corrigir erros de sintaxe.

 Quando essa caixa de seleção é marcada, você tem a opção de marcar a caixa de seleção **Mostrar erros como avisos**.

 **Mostrar erros como avisos** Quando essa caixa de seleção está marcada, os erros de JavaScript são mostrados como avisos em vez de erros na lista de erros.

 **Baixar referências remotas (por exemplo, http://) para arquivos no projeto de arquivos diversos** Quando essa caixa de seleção está marcada e, se você tiver um arquivo JavaScript aberto fora do contexto de um projeto, o Visual Studio baixará os arquivos JavaScript remotos referenciados no arquivo para fins de fornecimento de informações do IntelliSense. Se essa opção for selecionada, os arquivos serão baixados quando você incluí-los como uma referência no seu arquivo JavaScript.

> [!NOTE]
> Em projetos Web, os arquivos remotos referenciados no seu projeto são baixados por padrão.

## <a name="statement-completion"></a>Preenchimento de declaração
 Você pode usar essas opções para alterar o comportamento do preenchimento de declaração do IntelliSense.

## <a name="uielement-list"></a>Lista UIElement
 **Usar apenas Tab ou ENTER para confirmar** Quando essa caixa de seleção é marcada, o editor de código do JavaScript acrescenta instruções com itens selecionados na lista de conclusão somente depois de escolher a guia ou Inserir chave. Quando essa caixa de seleção não é marcada, outros caracteres, como ponto, vírgula, dois-pontos, parênteses de abertura e chave de abertura ({), também podem acrescentar instruções com os itens selecionados.

## <a name="references"></a>Referências
 Você pode usar essas opções para especificar os tipos de arquivo .js do IntelliSense que estão no escopo de diferentes tipos de projeto JavaScript. Geralmente, as referências do IntelliSense são usadas para oferecer suporte a objetos globais do IntelliSense. Também é possível usar essa página para definir a ordem de carregamento de scripts que devem ser carregados no tempo de execução e para adicionar arquivos de extensão do IntelliSense.

## <a name="uielement-list"></a>Lista UIElement
 **Grupos de referência** Esta opção especifica o tipo de grupo de referência. Há suporte para três grupos de referência:

 Você pode usar grupos de referência predefinidos para especificar se determinados arquivos .js do IntelliSense estão no escopo para diferentes projetos JavaScript. Quatro grupos de referência estão disponíveis:

- Implícitos (*versão* do Windows) para aplicativos [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] usando JavaScript. Os arquivos incluídos nesse grupo estão no escopo de cada arquivo .js aberto no Editor de Códigos para aplicativos do [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] que usam JavaScript.

- Implícito (Web), para projetos HTML5. Os arquivos incluídos nesse grupo estão no escopo de cada arquivo .js aberto no Editor de Códigos para esses tipos de projeto.

- Grupos de referência de atividade dedicada, para web workers HTML5. Os arquivos especificados nesse grupo estão no escopo de arquivos .js que têm uma referência explícita a um grupo de referência de atividade dedicada.

- Genérico, para outros tipos de projeto JavaScript.

  **Arquivos incluídos** Esta opção especifica a ordem em que os arquivos são carregados no contexto do serviço de idioma. Você pode configurar a ordem usando os botões **Remover**, **Subir** e **Descer**. Para que o IntelliSense funcione corretamente, um arquivo que depende de outro deve ser carregado depois do outro arquivo.

> [!CAUTION]
> Se um objeto for definido incondicionalmente em duas ou mais referências implícitas, a última referência nessa lista será usada para definir o objeto.

 **Adicionar uma referência ao grupo** Essa opção fornece uma maneira de adicionar outros arquivos IntelliSense. js navegando para os arquivos apropriados.

## <a name="see-also"></a>Veja também
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)
