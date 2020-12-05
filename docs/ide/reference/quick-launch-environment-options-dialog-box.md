---
title: Caixa de diálogo de início rápido, ambiente, opções
description: Saiba como usar a página início rápido na seção ambiente para pesquisar e executar rapidamente ações para ativos do IDE, como opções, modelos e menus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: e055906dd4cddabd16b39e3b2cad66d07dddd38d
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616740"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Caixa de diálogo de início rápido, ambiente, opções

Você pode usar o **Início Rápido** para pesquisar e executar rapidamente ações para ativos do IDE, como opções, modelos e menus. Não é possível usar o **Início Rápido** para pesquisar código e símbolos. A caixa de pesquisa de **Início Rápido** fica localizada no canto superior direito da barra de menus e pode ser acessada pressionando **Ctrl**+**Q**. Digite sua cadeia de caracteres de pesquisa na caixa. Para pesquisar cadeias de caracteres que contêm @, use “@@”.

O **Início Rápido** é habilitado por padrão quando você instala o Visual Studio. Na barra de menus, você pode exibir ou ocultar o **Início Rápido** escolhendo **Ferramentas** > **Opções**. Expanda o nó **Ambientes** e escolha **Início Rápido**. Marque ou desmarque a caixa de seleção **Habilitar Início Rápido**. Também é possível habilitar ou desabilitar categorias de pesquisa nesta página.

## <a name="category-list"></a>Lista de categorias

Os resultados da pesquisa do Início Rápido aparecem em quatro categorias: **Usados Recentemente**, **Menus**, **Opções** e **Documentos Abertos**, em conjunto com o número de itens na categoria. Para percorrer os resultados da pesquisa por categoria, escolha as teclas **Ctrl** + **Q** para mostrar todos os resultados da próxima categoria. Depois que a última categoria for exibida, **Ctrl** + **Q** mostrará alguns resultados de cada categoria. Pressione **Ctrl** + **Shift** + **p** para navegar pelas categorias na ordem inversa. Para exibir todos os resultados da pesquisa em uma categoria, escolha o nome da categoria.

É possível usar os seguintes atalhos para limitar a pesquisa a categorias específicas.

|Categoria|Atalho|Descrição do atalho|
|--------------|--------------| - |
|Usados Recentemente|@mru<br /><br /> Por exemplo, `@mru font`|Exibe até cinco dos itens que foram **Usados Recentemente**.|
|Menus|@menu<br /><br /> Por exemplo, `@menu project`|Limita a pesquisa a itens de menu.|
|Opções|@opt<br /><br /> Por exemplo, `@opt font`|Limita a pesquisa a configurações na caixa de diálogo **Opções**.|
|Documentos|@doc<br /><br /> Por exemplo, `@doc program.cs`|Limita a pesquisa a nomes de arquivo e caminhos de documentos abertos para os critérios de pesquisa, mas não pesquisa o texto dentro dos próprios arquivos.|

> [!NOTE]
> Você pode alterar as teclas de atalho na página **geral** do  >  **teclado** na caixa de diálogo **Opções** .

## <a name="show-previous-results"></a>Mostrar resultados anteriores

Por padrão, o termo de pesquisa que você inserir não persiste entre sessões de pesquisa. A cadeia de caracteres de pesquisa é apagada se você pesquisar um termo, mover o cursor para fora da área de **Início Rápido** e, depois, voltar. Para manter os resultados da pesquisa, acesse a caixa de diálogo **Opções**, escolha **Início Rápido** e, em seguida, marque a caixa de seleção **Mostrar resultados da pesquisa anterior quando o Início Rápido estiver ativado.** . Na próxima vez em que fizer uma pesquisa, deixe a área de Início Rápido e volte, o Início Rápido manterá o termo de pesquisa usado pela última vez e mostrará os resultados da pesquisa.
