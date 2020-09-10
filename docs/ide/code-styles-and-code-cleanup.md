---
title: Opções de estilo de código e limpeza de código
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 4faeff1e60fa77e3bf9e995c61c841f626468a1b
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743326"
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

Você pode definir as configurações de estilo do código por projeto usando um [arquivo EditorConfig](#code-styles-in-editorconfig-files) ou para todo o código que editar no Visual Studio na página [**Opções** do editor de texto](#code-styles-in-the-options-dialog-box). Para o código C#, você também pode configurar o Visual Studio para aplicar essas preferências de estilo de código usando os comandos **Limpeza de código** (Visual Studio 2019) e **Formatar documento** (Visual Studio 2017).

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Comportamento do editor no Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Estilos de código em arquivos EditorConfig

As [configurações de estilo de código](../ide/editorconfig-code-style-settings-reference.md) para .NET podem ser especificadas com a adição de um [EditorConfig](create-portable-custom-editor-options.md) ao seu projeto. Os arquivos EditorConfig são associados a uma base de códigos em vez de uma conta de personalização do Visual Studio. As configurações em um arquivo EditorConfig têm precedência sobre os estilos de código que são especificados na caixa de diálogo **Opções**. Use um arquivo EditorConfig quando quiser impor estilos de codificação para todos os fatores que contribuem para o seu repositório ou projeto.

::: moniker range=">=vs-2019"

Você pode preencher manualmente o arquivo EditorConfig ou gerar automaticamente um arquivo com base nas configurações de estilo de código definidas na caixa de diálogo **Opções** do Visual Studio. Esta página de opções está disponível em **ferramentas**  >  **Opções**  >  **Editor de texto** > [**C#** ou **Basic**] > **estilo de código**  >  **geral**. Clique em **Gerar arquivo .editorconfig das configurações** para gerar automaticamente um arquivo *.editorconfig* de estilo de codificação com base nas configurações na página **Opções**.

![Gerar arquivo editorconfig das configurações no Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Estilos de código na caixa de diálogo Opções

As preferências de estilo de código podem ser definidas para todos os seus projetos C# e do Visual Basic abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Na caixa de diálogo **Opções**, selecione **Editor de Texto** > [**C#** ou **Básico**] > **Estilo de Código** > **Geral**.

Cada item na lista mostra uma versão prévia da preferência quando selecionada:

::: moniker range="vs-2017"

![Opções de estilo de código](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opções de estilo de código](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

As opções definidas nessa janela são aplicáveis à sua conta de personalização do Visual Studio e não estão associadas a um determinado projeto ou base de códigos. Além disso, elas não são impostas no tempo de compilação, inclusive em builds de CI (integração contínua). Se você quiser associar as preferências de estilo de código ao seu projeto e ter os estilos impostos durante a criação, especifique as preferências em um [arquivo .editorconfig](#code-styles-in-editorconfig-files) que foi associado ao projeto.

### <a name="preference-and-severity"></a>Preferência e gravidade

Em cada configuração de estilo de código nessa página, é possível definir os valores de **Preferência** e **Gravidade** usando as listas suspensas de cada linha. A gravidade pode ser definida como **Somente Refatoração**, **Sugestão**, **Aviso** ou **Erro**. Se você quiser habilitar [Ações Rápidas](../ide/quick-actions.md) para um estilo de código, verifique se a configuração de **Gravidade** está definida como algo diferente de **Somente Refatoração**. O ícone de lâmpada de lâmpada de **ações rápidas** , lâmpada de erro de lâmpada de erro ou sinal de chave de fenda ![ ](media/light-bulb-dropdown.png) ![ ](media/error-bulb.png) ![ ](media/screwdriver.png) é exibido quando um estilo não preferencial é usado e você pode escolher uma opção na lista **ações rápidas** para reescrever automaticamente o código para o estilo preferencial.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Impor estilos de código na compilação

A partir do Visual Studio 2019 versão 16,8, que inclui o SDK do .NET 5,0 RC2, você pode [impor as convenções de codificação do .net na compilação](/dotnet/fundamentals/productivity/code-analysis.md#code-style-analysis) para todos os projetos .net. No momento da compilação, as violações de estilo de código .NET serão exibidas como avisos ou erros com um prefixo "IDE". Isso permite que você aplique estritamente estilos de código consistentes em sua codebase.

::: moniker-end

## <a name="apply-code-styles"></a>Aplicar estilos de código

::: moniker range="vs-2017"

Você pode configurar o comando **Formatar documento** (**Editar** > **Avançado** > **Formatar documento**) para aplicar as configurações de estilo de código (de um arquivo EditorConfig ou nas opções de **Estilo de código**), juntamente com a formatação regular que ele faz (por exemplo, recuo). Se um arquivo *.editorconfig* existir para o projeto, essas configurações terão precedência.

> [!NOTE]
> Aplicar os estilos de código usando o comando **Formatar documento** só está disponível para arquivos de código C#. Esse é um recurso experimental.

Configure quais definições você deseja que **Formatar documento** aplique na [página Opções de formatação](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Configurações de estilo de código para formatar documento no Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> As regras configuradas com uma gravidade de **Nenhum** não participam da limpeza de código, mas podem ser aplicadas individualmente por meio do menu **Ações rápidas e refatorações**.

Na primeira vez que você disparar o comando **Formatar documento**, uma barra amarela de informações solicitará que você defina as configurações de limpeza de código.

::: moniker-end

::: moniker range=">=vs-2019"

Para arquivos de código em C#, o Visual Studio 2019 tem um botão de **limpeza de código** na parte inferior do editor (teclado: **Ctrl** + **K**, **Ctrl** + **E**) para aplicar estilos de código de um arquivo EditorConfig ou da página de opções de **estilo de código** . Se um arquivo *.editorconfig* existir para o projeto, essas serão as configurações com precedência.

![Executar limpeza de código no Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> As regras configuradas com uma gravidade de **Nenhum** não participam da limpeza de código, mas podem ser aplicadas individualmente por meio do menu **Ações rápidas e refatorações**.

Primeiramente, configure quais estilos de código deseja aplicar (em um dos dois perfis) na caixa de diálogo **Configurar limpeza de código**. Para abrir essa caixa de diálogo, clique na seta de expansão ao lado do ícone de vassoura de limpeza de código e, em seguida, escolha **Configurar limpeza de código**.

![Configurar limpeza de código no Visual Studio 2019](media/configure-code-cleanup.png)

Depois de configurar a limpeza de código, você pode clicar no ícone Broom ou pressionar **Ctrl** + **K**, **Ctrl** + **E** para executar a limpeza de código. Você também pode fazer a limpeza de código em todo o projeto ou em toda a solução. Clique com o botão direito do mouse no nome do projeto ou da solução no **Gerenciador de Soluções**, selecione **Análise e Limpeza de Código** e selecione **Executar Limpeza de Código**.

![Fazer Limpeza de Código em todo projeto ou em toda solução](media/run-code-cleanup-project-solution.png)

Se quiser que as configurações de estilo de código sejam aplicadas sempre que salvar um arquivo, você apreciará a extensão [Limpeza de código ao salvar](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave).

::: moniker-end

## <a name="see-also"></a>Veja também

- [Ações Rápidas](../ide/quick-actions.md)
- [Configurações da Convenção de codificação .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamento do editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)
