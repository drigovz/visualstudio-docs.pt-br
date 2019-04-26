---
title: Caixa de diálogo de início rápido, ambiente, opções
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: a67e909dc43f17e12dd63b7a8a3b2e8a4afacc5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969040"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Caixa de diálogo de início rápido, ambiente, opções

Você pode usar o **Início Rápido** para pesquisar e executar rapidamente ações para ativos do IDE, como opções, modelos e menus. Não é possível usar o **Início Rápido** para pesquisar código e símbolos. A caixa de pesquisa de **Início Rápido** fica localizada no canto superior direito da barra de menus e pode ser acessada pressionando **Ctrl**+**Q**. Digite sua cadeia de caracteres de pesquisa na caixa. Para pesquisar cadeias de caracteres que contêm @, use “@@”.

O **Início Rápido** é habilitado por padrão quando você instala o Visual Studio. Na barra de menus, você pode exibir ou ocultar o **Início Rápido** escolhendo **Ferramentas** > **Opções**. Expanda o nó **Ambientes** e escolha **Início Rápido**. Marque ou desmarque a caixa de seleção **Habilitar Início Rápido**. Também é possível habilitar ou desabilitar categorias de pesquisa nesta página.

## <a name="category-list"></a>Lista de Categorias

Os resultados da pesquisa do Início Rápido são exibidos em quatro categorias: **Usados Recentemente**, **Menus**, **Opções** e **Documentos Abertos**, juntamente com o número de itens na categoria. Para percorrer os resultados da pesquisa por categoria, escolha as teclas **Ctrl**+**Q** para exibir todos os resultados da categoria seguinte. Depois que a última categoria aparecer, pressionar **Ctrl**+**Q** exibirá alguns resultados de cada categoria. Pressione **Ctrl**+**Shift**+**Q** para navegar pelas categorias na ordem oposta. Para exibir todos os resultados da pesquisa em uma categoria, escolha o nome da categoria.

É possível usar os seguintes atalhos para limitar a pesquisa a categorias específicas.

|Categoria|Atalho|Descrição do atalho|
|--------------|--------------| - |
|Usados Recentemente|@mru<br /><br /> Por exemplo, `@mru font`|Exibe até cinco dos itens que foram **Usados Recentemente**.|
|Menus|@menu<br /><br /> Por exemplo, `@menu project`|Limita a pesquisa a itens de menu.|
|Opções|@opt<br /><br /> Por exemplo, `@opt font`|Limita a pesquisa a configurações na caixa de diálogo **Opções**.|
|Documentos|@doc<br /><br /> Por exemplo, `@doc program.cs`|Limita a pesquisa a nomes de arquivo e caminhos de documentos abertos para os critérios de pesquisa, mas não pesquisa o texto dentro dos próprios arquivos.|

> [!NOTE]
> Você pode alterar as teclas de atalho na página **Geral**  > **Teclado** na caixa de diálogo **Opções**.

## <a name="show-previous-results"></a>Mostrar resultados anteriores

Por padrão, o termo de pesquisa que você inserir não persiste entre sessões de pesquisa. A cadeia de caracteres de pesquisa é apagada se você pesquisar um termo, mover o cursor para fora da área de **Início Rápido** e, depois, voltar. Para manter os resultados da pesquisa, acesse a caixa de diálogo **Opções**, escolha **Início Rápido** e, em seguida, marque a caixa de seleção **Mostrar resultados da pesquisa anterior quando o Início Rápido estiver ativado.** . Na próxima vez em que fizer uma pesquisa, deixe a área de Início Rápido e volte, o Início Rápido manterá o termo de pesquisa usado pela última vez e mostrará os resultados da pesquisa.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)
