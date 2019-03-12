---
title: Preferências de estilo de código
ms.date: 03/10/2017
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 1f5ad2f5860c148d4bb9d0ee026eee9b1e83c74c
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223124"
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

As preferências de estilo de código podem ser definidas em seus projetos em C# e do Visual Basic, abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Na caixa de diálogo **Opções**, selecione **Editor de Texto** > [**C#** ou **Básico**] > **Estilo de Código** > **Geral**. As opções definidas nessa janela aplicam-se apenas ao computador local.

Cada item na lista mostra uma versão prévia da preferência quando selecionada:

![Opções de estilo de código](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Comportamento do editor no Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Preferência e gravidade

Para cada item, é possível definir os valores **Preferência** e **Severidade** usando as listas suspensas de cada linha. A severidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro**. Se você quiser habilitar [Ações Rápidas](../ide/quick-actions.md) para um estilo de código, verifique se a configuração de **Severidade** está definida como algo diferente de **Nenhuma**. O ícone de lâmpada ![Ícone de lâmpada](media/vs2015_lightbulbsmall.png) **Ações Rápidas**, de lâmpada de erro ![lâmpada de erro](media/error-bulb.png) ou de chave de fenda ![chave de fenda](media/screwdriver.png) é exibido quando um estilo não preferencial é usado. Você pode escolher uma opção na lista **Ações Rápidas** para reescrever o código automaticamente no estilo preferencial.

## <a name="editorconfig-files"></a>Arquivos EditorConfig

As configurações de estilo de código para o .NET também podem ser gerenciadas com um arquivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). As configurações no arquivo EditorConfig têm precedência sobre as opções selecionadas na caixa de diálogo **Opções**. É possível usar um arquivo EditorConfig para impor e configurar o estilo de codificação de todo o repositório ou projeto.

## <a name="format-document-command"></a>Comando Formatar Documento

Configure o comando **Formatar Documento** (**Editar** > **Avançado** > **Formatar Documento**) para executar uma limpeza de código adicional em um arquivo, como remover e classificar instruções using ou aplicar preferências de estilo de código. Você pode definir quais configurações deseja que **Formatar Documento** aplique na [página Opções de formatação](reference/options-text-editor-csharp-formatting.md#format-document-settings).

A limpeza de código respeita as configurações definidas em um arquivo *.editorconfig* ou a falta dessa regra ou arquivo, conforme a definição em **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > [**Estilos de Código** ou **Formatação**].

Na primeira vez que você dispara o comando **Formatar Documento** no Visual Studio, uma barra amarela de informações solicita que você defina as configurações de limpeza de código.

> [!TIP]
> As regras configuradas como **none** em um arquivo *.editorconfig* não participam da limpeza de código, mas podem ser aplicadas individualmente por meio do menu **Ações Rápidas e Refatorações**.

## <a name="see-also"></a>Consulte também

- [Ações rápidas](../ide/quick-actions.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamento do editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)