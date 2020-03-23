---
title: Opções de formatação do editor de C#
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1176232eb3354a9b425e9432eb83037367ee7706
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303074"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Caixa de diálogo \> opções: \> Formatação do estilo de código do editor de texto C# \>

Use a página de opções de **Formatação** e suas subpáginas ([**Recuo**](#indentation-page), **Novas Linhas**, **Espaçamento** e **Encapsulamento**) para definir opções de formatação de código no editor de código.

Para acessar esta página de opções, escolha **Opções** > de**ferramentas** na barra de menus. Na caixa de diálogo **Opções**, escolha **Editor de Texto** > **C#** > **Estilo de Código** > **Formatação**.

> [!TIP]
> As subpáginas **Recuo**, **Novas Linhas**, **Espaçamento** e **Quebra Automática** exibem uma janela de visualização na parte inferior que mostra o efeito de cada opção. Para usar a janela de visualização, selecione uma opção de formatação. A janela de visualização mostra um exemplo da opção selecionada. Quando você altera uma configuração selecionando um botão de opção ou marcando uma caixa de seleção, a janela de visualização é atualizada para mostrar o efeito da nova configuração.

## <a name="formatting-general-page"></a>Página Formatação (Geral)

### <a name="general-settings"></a>Configurações gerais

Essas configurações afetam *quando* o editor de códigos aplica opções de formatação ao código.

|Rótulo|Descrição|
|-----------|-----------------|
|**Formatar automaticamente ao digitar**|Quando estiver desmarcada, as opções **formatar instrução em ;** e **formatar bloco em }** estarão desabilitadas.|
|**Formatar instrução automaticamente em ;**|Quando selecionada, formata as instruções na conclusão de acordo com as opções de formatação selecionadas para o editor.|
|**Formatar bloco automaticamente em }**|Quando selecionada, formata blocos de código de acordo com as opções de formatação selecionadas para o editor assim que você conclui o bloco de código.|
|**Formatar automaticamente na devolução**|Quando selecionada, formata o texto quando **Enter** é pressionado, de acordo com as opções de formatação selecionadas para o editor.|
|**Formatar automaticamente ao colar**|Quando selecionada, formata o texto que é colado no editor de acordo com as opções de formatação selecionadas para o editor.|

::: moniker range="vs-2019"

Se você aplicou as configurações de estilo de código para arquivos C# usando o comando **Formatar Documento** no Visual Studio 2017, essa funcionalidade agora está disponível como [**Limpeza de Código**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Configurações de Formatar Documento

Essas configurações definem o comando **Formatar Documento** para executar a limpeza de código adicional em um arquivo. Para obter mais informações sobre como essas configurações são aplicadas, confira [Comando Formatar Documento](../code-styles-and-code-cleanup.md#apply-code-styles).

|Rótulo|Descrição|EditorConfig e ferramentas correspondentes > Regras de opções|
|-----------|-----------------|-----------------|-----------------|
|**Aplicar todas as regras de formatação de C# (recuo, quebra automática, espaçamento)**|O comando **Formatar Documento** sempre corrige os problemas de formatação. Essa configuração não pode ser alterada.| [Principais opções do EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Opções de formatação do EditorConfig do .NET](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**Opções** > **de ferramentas** > **Editor de** > texto**C#** > **Formatação** > [**Recuo** ou **Novas Linhas** ou **Espaçamento** ou **Embrulhamento**]|
|**Executar limpeza de código de adição durante a formatação**|Quando selecionada, aplica correções para as regras especificadas abaixo no comando **Edit.FormatDocument**.| N/D |
|**Remova os usos desnecessários**|Quando selecionada, remove as diretivas `using` desnecessários quando **Edit.FormatDocument** é disparado.| N/D |
|**Classificar usos**|Quando selecionada, classifica as diretivas `using` quando **Edit.FormatDocument** é disparado.| dotnet_sort_system_directives_first<br/><br/>**Opções** > **de ferramentas** > Editor de > **texto****C#** > **Advanced** > Place **'System' diretivas primeiro ao classificar usos** |
|**Adicionar/remover chaves de instruções de controle de única linha**|Quando selecionado, adiciona ou remove as chaves das instruções de controle de única linha quando **Edit.FormatDocument** é disparado.| csharp_prefer_braces<br/><br/>**Opções** > **de ferramentas** > **Editor de texto** > **C#** > **Preferências** > **de bloco de código de código** > **Preferência satisfazê-lo** |
|**Adicionar modificadores de acessibilidade**|Quando selecionada, adiciona os modificadores de acessibilidade ausentes quando **Edit.FormatDocument** é disparado.| dotnet_style_require_accessibility_modifiers |
|**Classificar modificadores de acessibilidade**|Quando selecionada, classifica os modificadores de acessibilidade quando **Edit.FormatDocument** é disparado.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Aplicar preferências de corpo de expressão/bloco**|Quando selecionada, converte os membros no corpo da expressão em corpos de bloco, ou vice-versa, quando **Edit.FormatDocument** é disparado.| [Opções do EditorConfig para membro no corpo da expressão](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**Opções** > **de ferramentas** > **Editor de** > texto**C#** > **Preferências** > de expressão**de estilo** > de código**Use o corpo de expressão para métodos, construtores, etc.** |
|**Aplicar preferências de tipo implícitas/explícitas**|Quando selecionada, converte `var` no tipo explícito, ou vice-versa, quando **Edit.FormatDocument** é disparado.| [Opções do EditorConfig para tipo explícito](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**Opções** > **de ferramentas** > Editor de > **texto****C#** > **Preferências de estilo de** > código **'var'** |
|**Aplicar preferências de variáveis 'out' embutidas**|Quando selecionada, embute as variáveis `out` onde possível quando **Edit.FormatDocument** é disparado.| csharp_style_inlined_variable_declaration<br/><br/>**Opções** > **de ferramentas** > **Editor de** > texto**C#** > **Preferências** > variáveis**de estilo** > de código**Prefira declaração variável inforrada** |
|**Aplicar preferências de tipo de linguagem/estrutura**|Quando selecionada, converte tipos de linguagem em tipos de estrutura, ou vice-versa, quando **Edit.FormatDocument** é disparado.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Opções** > **de ferramentas** > **Editor de texto** > **C#** > **Estilo de** > código**predefinido preferências de tipo** |
|**Aplicar preferências de inicialização de objeto/coleção**|Quando selecionada, usa os inicializadores de objeto e de coleção sempre que possível quando **Edit.FormatDocument** é disparado.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Opções** > **de ferramentas** > **Editor de texto** > **C#** > **Preferências** > de expressão**de estilo** > de**código Prefira inicializador de objetos** ou **Prefira inicializador de coleção** |
|**Aplicar preferências de qualificação 'this.'**|Quando marcada, aplica as preferências de `this.` quando **Edit.FormatDocument** é disparado.| [Opções do EditorConfig para a qualificação this.](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**Opções** > **de ferramentas** > Editor de**texto** > **C#** > **Estilo de** > código **'isso.'** |
|**Tornar campos particulares readonly quando possível**|Quando selecionada, torna os campos particulares `readonly` sempre que possível quando **Edit.FormatDocument** é disparado.| dotnet_style_readonly_field<br/><br/>**Opções** > **de ferramentas** > **Editor de texto** > **C#** > **Preferências** > **de campo de estilo de** > código**Prefira leitura apenas** |
|**Remover conversões desnecessárias**|Quando selecionada, remove as conversões desnecessárias sempre que possível quando **Edit.FormatDocument** é disparado.| N/D |
|**Remover variáveis não utilizadas**|Quando selecionada, remove as variáveis que não são usadas quando **Edit.FormatDocument** é disparado.| N/D |

![Configurações de limpeza de código para C# no Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Página Recuo

As opções de recuo nessa página se aplicam quando o código é formatado automaticamente. Um exemplo de quando o código é formatado automaticamente é quando você cola o código no arquivo e a opção **Formatar automaticamente ao colar** está selecionada. (A opção **Formatar automaticamente ao colar** está sob **Formatação** > **Geral**.)

![Opções de recuo do editor de texto em C# no Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Há também opções de recuo na página**de opções De guias** **do Editor de** > texto**C#.** >  Essas opções determinam apenas onde o editor de códigos coloca o cursor quando você pressiona **Enter** no final de uma linha.
>
> ![Opções de guias do editor de texto em C# no Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Confira também

- [Caixa de diálogo Geral, Meio Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
