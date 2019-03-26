---
title: Preferências de estilo de código
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: a7a478e8d3575e70a11ec776d59337ae93e7a677
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57873354"
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

As preferências de estilo de código podem ser definidas em seus projetos em C# e do Visual Basic, abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Na caixa de diálogo **Opções**, selecione **Editor de Texto** > [**C#** ou **Básico**] > **Estilo de Código** > **Geral**. Cada item na lista mostra uma versão prévia da preferência quando selecionada:

![Opções de estilo de código](media/code-style-quick-actions-dialog.png)

As opções definidas nessa janela são aplicáveis à sua conta de personalização do Visual Studio e não estão associadas a um determinado projeto ou base de códigos. Além disso, elas não são impostas no tempo de compilação, inclusive em builds de CI (integração contínua). Se você quiser associar as preferências de estilo de código ao seu projeto e impor os estilos durante a compilação, especifique as preferências em um [arquivo .editorconfig](#editorconfig-files).

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Comportamento do editor no Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Preferência e gravidade

Para cada item, é possível definir os valores **Preferência** e **Severidade** usando as listas suspensas de cada linha. A severidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro**. Se você quiser habilitar [Ações Rápidas](../ide/quick-actions.md) para um estilo de código, verifique se a configuração de **Severidade** está definida como algo diferente de **Nenhuma**. O ícone de lâmpada ![Ícone de lâmpada](media/light-bulb-dropdown.png) **Ações Rápidas**, de lâmpada de erro ![lâmpada de erro](media/error-bulb.png) ou de chave de fenda ![chave de fenda](media/screwdriver.png) é exibido quando um estilo não preferencial é usado. Você pode escolher uma opção na lista **Ações Rápidas** para reescrever o código automaticamente no estilo preferencial.

## <a name="editorconfig-files"></a>Arquivos EditorConfig

As configurações de estilo de código para .NET também podem ser especificadas com a adição de um arquivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ao seu projeto. Esses arquivos são associados a uma base de códigos em vez de uma conta de personalização do Visual Studio. As configurações no arquivo EditorConfig têm precedência sobre as opções selecionadas na caixa de diálogo **Opções**. Use um arquivo EditorConfig quando quiser impor estilos de codificação para todos os fatores que contribuem para o seu repositório ou projeto.

## <a name="format-document-command"></a>Comando Formatar Documento

Configure o comando **Formatar Documento** (**Editar** > **Avançado** > **Formatar Documento**) para executar uma limpeza de código adicional em um arquivo, como remover e classificar instruções using ou aplicar preferências de estilo de código. Você pode definir quais configurações deseja que **Formatar Documento** aplique na [página Opções de formatação](reference/options-text-editor-csharp-formatting.md#format-document-settings).

A limpeza de código respeita as configurações definidas em um arquivo *.editorconfig* ou a falta dessa regra ou arquivo, conforme a definição em **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > [**Estilos de Código** ou **Formatação**].

Na primeira vez que você dispara o comando **Formatar Documento** no Visual Studio, uma barra amarela de informações solicita que você defina as configurações de limpeza de código.

> [!TIP]
> As regras configuradas com gravidade **Nenhuma** não participam da limpeza de código, mas podem ser aplicadas individualmente por meio do menu **Ações Rápidas e Refatorações**.

## <a name="see-also"></a>Consulte também

- [Ações rápidas](../ide/quick-actions.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamento do editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)