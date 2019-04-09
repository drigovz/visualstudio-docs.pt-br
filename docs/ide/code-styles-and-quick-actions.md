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
ms.openlocfilehash: 689bdb62d5a4bc9aea21da67e8e5e844660756d6
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647304"
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

As preferências de estilo de código podem ser definidas em seus projetos em C# e do Visual Basic, abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Na caixa de diálogo **Opções**, selecione **Editor de Texto** > [**C#** ou **Básico**] > **Estilo de Código** > **Geral**.

Cada item na lista mostra uma versão prévia da preferência quando selecionada:

::: moniker range="vs-2017"

![Opções de estilo de código](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opções de estilo de código](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

As opções definidas nessa janela são aplicáveis à sua conta de personalização do Visual Studio e não estão associadas a um determinado projeto ou base de códigos. Além disso, elas não são impostas no tempo de compilação, inclusive em builds de CI (integração contínua). Se você quiser associar as preferências de estilo de código ao seu projeto e impor os estilos durante a compilação, especifique as preferências em um [arquivo .editorconfig](#editorconfig-files).

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Comportamento do editor no Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="editorconfig-files"></a>Arquivos EditorConfig

As configurações de estilo de código para .NET também podem ser especificadas com a adição de um arquivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ao seu projeto.

::: moniker range=">=vs-2019"

Clique em **Gerar arquivo .editorconfig nas configurações** para gerar automaticamente um arquivo .editorconfig de estilo de codificação baseado nas opções que você definiu nesta página **Opções**.

![Gerar o arquivo editorconfig nas configurações no VS2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

Os arquivos EditorConfig são associados a uma base de códigos em vez de uma conta de personalização do Visual Studio. As configurações em um arquivo EditorConfig têm preferência sobre as opções selecionadas na caixa de diálogo **Opções**. Use um arquivo EditorConfig quando quiser impor estilos de codificação para todos os fatores que contribuem para o seu repositório ou projeto.

## <a name="preference-and-severity"></a>Preferência e gravidade

Em cada configuração de estilo de código nessa página, é possível definir os valores de **Preferência** e **Gravidade** usando as listas suspensas de cada linha. A gravidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro**. Se você quiser habilitar [Ações Rápidas](../ide/quick-actions.md) para um estilo de código, verifique se a configuração de **Gravidade** está definida como algo diferente de **Nenhuma**. O ícone de lâmpada ![Ícone de lâmpada](media/light-bulb-dropdown.png) **Ações Rápidas**, de lâmpada de erro ![lâmpada de erro](media/error-bulb.png) ou de chave de fenda ![chave de fenda](media/screwdriver.png) é exibido quando um estilo não preferencial é usado. Você pode escolher uma opção na lista **Ações Rápidas** para reescrever o código automaticamente no estilo preferencial.

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