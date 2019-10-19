---
title: Opções, Editor de Texto, C#, Avançado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662329"
---
# <a name="options-text-editor-c-advanced"></a>Opções, Editor de Texto, C#, Avançado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use essa caixa de diálogo para modificar as configurações de formatação do editor, refatoração de código e comentários da documentação XML do Visual C#. Para acessar essa caixa de diálogo, clique em **Opções** no menu **Ferramentas**, expanda a pasta **Editor de Texto**, expanda **C#** e, em seguida, clique em **Avançado**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>Estrutura de tópicos
 Insira o modo de estrutura de tópicos quando os arquivos são abertos quando selecionado, descreve automaticamente o arquivo de código, que cria blocos recolhíveis de código. Na primeira vez que um arquivo é aberto, blocos #regions e blocos de códigos inativos são recolhidos.

## <a name="editor-help"></a>Ajuda do Editor
 Os erros de sublinhado no editor identificam erros de compilação no código. Quando essa opção é selecionada, os sublinhados ondulados são exibidos em cores que têm significados específicos:

- Erros de análise são vermelhos.

- Erros de build são azuis.

- Avisos de build são verdes.

- Edições de [Editar e Continuar](../../debugger/edit-and-continue.md) inválidas são roxas.

  Mova o ponteiro sobre o segmento de código sublinhado para ver uma ToolTip com informações sobre o erro.

  Mostrar erros semânticos ao vivo identifica determinados erros de compilação sem compilação explícita, por exemplo, declarando e usando um tipo desconhecido ou fazendo referência a uma propriedade desconhecida.

  Realçar referências ao símbolo sob o cursor quando o cursor estiver posicionado dentro de um símbolo ou quando você clicar em um símbolo, todas as instâncias desse símbolo no arquivo de código serão realçadas.

## <a name="refactoring"></a>Refatoração
 Verificar os resultados da refatoração exibe a caixa de diálogo **resultados da verificação** quando você tenta refatorar o código que contém erros de compilação ou quando a refatoração faz com que uma referência de código seja associada a algo diferente de sua associação original.

 Avisar sobre membros com referências geradas pelo compilador exibe uma caixa de diálogo de aviso quando você tenta refatorar um membro que tem o mesmo nome que uma referência gerada pelo compilador.

## <a name="xml-documentation-comments"></a>Comentários da documentação XML
 Gerar comentários de documentação XML para///quando selecionado, insere o \<summary > marca de início e término automaticamente para comentários de documentação XML depois de digitar a introdução de comentário///. Para obter mais informações sobre a documentação XML, consulte [Comentários da documentação XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Implementar interface
 O código gerado por surround com #region insere um #region \<*nome da interface*> membro ao redor dos métodos quando implementar interface ou implementar interface explicitamente é usado.

## <a name="organize-usings"></a>Organizar Usos
 Coloque as diretivas ' System ' primeiro ao classificar usando quando selecionado, `System` usando diretivas aparecem antes de outras usando diretivas. Para obter mais informações, consulte [Classificar usos](../../misc/sort-usings.md).

## <a name="see-also"></a>Veja também
 [Comentários de documentação XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [definindo opções de editor específicas da linguagem](../../ide/reference/setting-language-specific-editor-options.md) [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
