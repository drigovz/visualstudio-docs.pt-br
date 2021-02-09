---
title: Codificando caracteres de quebra de linha
description: Saiba mais sobre os caracteres que o Visual Studio interpreta como quebras de linha e como a codificação original e os caracteres de quebra de linha são mantidos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e466439469db66e8e871115abc9828988f24b546
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924747"
---
# <a name="encodings-and-line-endings"></a>Codificações e términos de linha

Os seguintes caracteres são interpretados como quebras de linha no Visual Studio:

- CR LF: retorno de carro + alimentação de linha, caracteres Unicode 000D + 000A

- LF: alimentação de linha, caractere Unicode 000A

- NEL: próxima linha, caractere Unicode 0085

- LS: separador de linha, caractere Unicode 2028

- PS: separador de parágrafo, caractere Unicode 2029

O texto copiado de outros aplicativos mantém a codificação original e os caracteres de quebra de linha. Por exemplo, quando você copia texto do Bloco de notas e o cola em um arquivo de texto no Visual Studio, o texto tem as mesmas configurações que ele tinha no Bloco de notas.

Ao abrir um arquivo que tem caracteres de quebra de linha diferentes, talvez você veja uma caixa de diálogo que pergunta se os caracteres de quebra de linha inconsistentes devem ser normalizados e quais os tipo de quebras de linha você deseja escolher.

## <a name="advanced-save-options"></a>Opções avançadas de salvamento

Você pode usar a   >  caixa de diálogo **Opções de salvamento avançadas** do arquivo para determinar o tipo de caracteres de quebra de linha desejado. Também é possível alterar a codificação de um arquivo com as mesmas configurações.

![caixa de diálogo Opções avançadas de salvar](media/line_endings.png)

> [!NOTE]
> Se você não vir **Opções Avançadas de Salvamento** no menu **Arquivo**, você poderá adicioná-la. 
> 1. Escolha **ferramentas**, **Personalizar**, 
> 1. Escolha a guia **comandos** , selecione o botão de opção **barra de menus** e, na lista suspensa correspondente, escolha **arquivo**. Escolha o botão **Adicionar comando** . 
> 1. Na caixa de diálogo **Adicionar Comando**, em **Categorias**, escolha **Arquivo** e, em seguida, na lista **Comandos**, escolha **Opções Avançadas de Salvamento**. Escolha o botão **OK** .
> 1. Use os botões **mover para cima** e mover para **baixo** para mover o comando para qualquer lugar no menu. Escolha **Fechar** para fechar a caixa de diálogo **Personalizar**. 
> Para obter mais informações, consulte [Personalizar menus e barras de ferramentas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Como alternativa, você pode acessar a caixa de diálogo **Opções de salvamento avançadas** escolhendo **arquivo**  >  **Salvar \<file\> como**. Na caixa de diálogo **salvar arquivo como** , escolha o triângulo suspenso ao lado do botão **salvar** e, em seguida, escolha **salvar com codificação**.

## <a name="see-also"></a>Confira também

- [Recursos do editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
