---
title: Localizando referências no código
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4ef16ef88e871778fd4e0c755ffb156c374109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592029"
---
# <a name="find-references-in-your-code"></a>Localizar referências no seu código

Você pode usar o comando **Localizar Todas as Referências** para localizar onde elementos de código específicos são referenciados em toda a base de código. O comando **Localizar Todas as Referências** está disponível no menu de contexto (acessado com o clique do botão direito do mouse) do elemento cujas referências você deseja localizar. Ou, se você estiver usando o teclado, pressione **Shift + F12**.

Os resultados aparecem em uma janela de ferramentas chamada ** \<element> References**, em que *Element* é o nome do item que você está pesquisando. Uma barra de ferramentas na janela **referências** permite que você:
- Altere o escopo da pesquisa em uma caixa de listagem suspensa. É possível optar por examinar apenas documentos alterados até a solução inteira.
- Copie o item referenciado selecionado ao selecionar o botão **Copiar**.
- Escolha os botões para acessar o local anterior ou seguinte na lista. Também é possível pressionar as teclas **F8** e **Shift + F8** para fazer isso.
- Remova todos os filtros nos resultados retornados, escolhendo o botão **Limpar Todos os Filtros**.
- Altere como os itens retornados são agrupados escolhendo uma configuração na caixa de listagem suspensa **Agrupar por:** .
- Mantenha a janela de resultados da pesquisa atual ao escolher o botão **Manter Resultados**. Ao selecionar este botão, os resultados da pesquisa atual ficam nessa janela, e novos resultados da pesquisa são exibidos em uma nova janela de ferramentas.
- Pesquisar cadeias de caracteres nos resultados da pesquisa inserindo texto na caixa de texto **Pesquisar Localizar Todas as Referências**.

Também é possível passar o mouse sobre qualquer resultado da pesquisa para obter uma visualização da referência.

![Janela de ferramentas Localizar Todas as Referências](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Navegue até referências
Você pode usar os seguintes métodos para navegar para as referências na janela **referências**:

- Pressione **F8** para acessar a próxima referência ou **Shift + F8** para acessar a referência anterior.
- Pressione a tecla **Enter** em uma referência ou clique duas vezes nela para acessá-la no código.
- No menu do clique com o botão direito (menu de contexto) de uma referência, escolha os comandos **Ir para Local Anterior** ou **Ir para Próximo Local**.
- Escolha as teclas de seta para **cima** e **seta para baixo** (se elas estiverem habilitadas na caixa de diálogo **Opções** ). Para habilitar essa funcionalidade, na barra de menus, escolha **ferramentas**  >  **Opções**  >  **Environment**  >  **guias de ambiente e**  >  a**guia Visualização**do Windows e, em seguida, selecione **permitir novos arquivos a serem abertos na guia Visualizar** e **visualize os arquivos selecionados em caixas de pesquisa de resultados** .

## <a name="change-reference-groupings"></a>Alterar agrupamentos de referência
Por padrão, as referências são agrupadas por projetos, depois por definição. No entanto, você pode alterar essa ordem de agrupamento alterando a configuração na caixa de listagem suspensa **Agrupar por:** na barra de ferramentas. Por exemplo, é possível alterá-la na configuração padrão de **Projeto em vez de definição** para **Definição em vez de projeto** e também para outras configurações.

**Definição** e **Projeto** são dois agrupamentos padrão usados, mas é possível adicionar outros ao escolher o comando **Agrupamento** no menu do clique com o botão direito ou de contexto do item selecionado. Pode ser útil adicionar mais agrupamentos se sua solução tem muitos arquivos e caminhos.

## <a name="filter-by-reference-type-in-net"></a>Filtrar por tipo de referência no .NET
No C# ou Visual Basic, a janela Localizar Referências tem uma coluna de tipo em que ela lista o tipo de referência encontrada. Esta coluna pode ser usada para filtrar por tipo de referência, clicando no ícone de filtro que aparece ao passar o mouse sobre o cabeçalho da coluna. As referências podem ser filtradas por Leitura, Gravação, Referência, Nome, Namespace e Tipo.

![Encontrar a coluna Tipo da janela Referências ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Confira também

- [Código de navegação](../ide/navigating-code.md)
