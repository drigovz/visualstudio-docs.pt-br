---
title: Localizar e substituir texto, e seleção de vários cursores
description: Saiba mais sobre o recurso Localizar e substituir e como usá-lo para localizar e substituir instâncias de um padrão.
ms.custom: SEO-VS-2020
ms.date: 10/17/2020
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 534d25c97977d058f0b4137955e44e3d544b3878
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932599"
---
# <a name="find-and-replace-text"></a>Localizar e substituir texto

Localize e substitua um texto no editor do Visual Studio usando [Localizar e Substituir](#find-and-replace-control) (**Ctrl**+**F** ou **Ctrl**+**H**) ou [Localizar/Substituir em Arquivos](#find-in-files-and-replace-in-files) (**Ctrl**+**Shift**+**F** ou **Ctrl**+**Shift**+**H**). Localize e substitua também apenas *algumas* instâncias de um padrão usando a *[seleção de vários sinais de interpolação](#multi-caret-selection)*.

> [!TIP]
> Se você está renomeando os símbolos de código, como variáveis e métodos, é melhor *[refatorá-los](../ide/reference/rename.md)* em vez de usar o recurso Localizar e Substituir. A refatoração é inteligente e reconhece o escopo, enquanto o recurso Localizar e Substituir substitui cegamente todas as instâncias.

A funcionalidade Localizar e Substituir está disponível no editor, em algumas outras janelas baseadas em texto, como as janelas **Localizar Resultados**, em janelas do designer como o Designer XAML e o Designer de Formulários do Windows e nas janelas de ferramentas.

É possível definir o escopo das pesquisas para o documento atual, a solução atual ou um conjunto personalizado de pastas. Também é possível especificar um conjunto de extensões de nome de arquivo para pesquisas em vários arquivos. Personalize a sintaxe de pesquisa usando [expressões regulares](../ide/using-regular-expressions-in-visual-studio.md) do .NET.

> [!TIP]
> A caixa [Localizar/Comando](../ide/find-command-box.md) está disponível como um controle de barra de ferramentas, mas não fica visível por padrão. Para exibir a caixa **Localizar/Comando**, selecione **Adicionar ou Remover Botões** na barra de ferramentas **Padrão** e, em seguida, selecione **Localizar**.

## <a name="find-and-replace-control"></a>Controle Localizar e Substituir

- Pressione **Ctrl** + **F** como um atalho para *Localizar* uma cadeia de caracteres no arquivo atual.
- Pressione **Ctrl** + **H** como um atalho para *Localizar e substituir* uma cadeia de caracteres no arquivo atual.

O controle **Localizar e Substituir** aparece no canto superior direito da janela do editor de código. Ele realça imediatamente todas as ocorrências da cadeia de caracteres de pesquisa fornecida no documento atual. Você pode navegar de uma ocorrência para outra escolhendo o botão **Localizar próximo** ou o botão **Localizar anterior** no controle de pesquisa.

![Localizar e Substituir no Visual Studio](media/find-and-replace-box.png)

Você pode acessar opções de substituição escolhendo o botão ao lado da caixa de texto **Localizar**. Para fazer uma substituição por vez, escolha o botão **Substituir próximo** ao lado da caixa de texto **Substituir**. Para substituir todas as correspondências, escolha o botão **Substituir tudo**.

Para alterar a cor de realce das correspondências, escolha o menu **Ferramentas**, selecione **Opções** e, em seguida, escolha **Ambiente** e selecione **Fontes e Cores**. Na lista **Mostrar configurações de**, selecione **Editor de Texto** e, na lista **Exibir Itens**, selecione **Localizar Realce (Extensão)**.

### <a name="search-tool-windows"></a>Janelas de ferramentas de pesquisa

Use o controle **Localizar** em janelas de texto ou de código, como janelas **Saída** e janelas **Localizar Resultados** selecionando **Editar** > **Localizar e Substituir** ou pressionando **Ctrl+F**.

Uma versão do controle **Localizar** também está disponível em algumas janelas de ferramentas. Por exemplo, você pode filtrar a lista de controles na janela **Caixa de Ferramentas** inserindo o texto na caixa de pesquisa. Outras janelas de ferramentas que permitem pesquisar seu conteúdo incluem o **Gerenciador de Soluções**, a janela **Propriedades** e o **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Localizar nos arquivos e substituir nos arquivos

- Pressione **Ctrl** + **Shift** + **F** como um atalho para *Localizar* uma cadeia de caracteres em vários arquivos.
- Pressione **Ctrl** + **Shift** + **H** como um atalho para *Localizar e substituir* uma cadeia de caracteres em vários arquivos.

**Localizar/substituir em Arquivos** funciona como o controle **Localizar e Substituir**, mas você pode definir um escopo para a pesquisa. Você pode pesquisar não apenas o arquivo atual aberto no editor, mas também todos os documentos abertos, toda a solução, o projeto atual e conjuntos de pastas selecionados. Você também pode pesquisar por extensão de nome de arquivo. Para acessar a caixa de diálogo **Localizar/Substituir em Arquivos**, selecione **Localizar e Substituir** no menu **Editar** (ou pressione **Ctrl**+**Shift**+**F**).

![Localizar em Arquivos no Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Localizar Resultados

Quando você escolhe **Localizar tudo**, uma janela **Localizar Resultados** é aberta e lista as correspondências da pesquisa. Selecionar um resultado na lista exibe o arquivo associado e realça a correspondência. Se o arquivo ainda não estiver aberto para edição, ele será aberto em uma guia de visualização no lado direito da guia. É possível usar o controle **Localizar** para pesquisar na lista **Localizar Resultados**.

### <a name="create-custom-search-folder-sets"></a>Criar conjuntos de pastas de pesquisa personalizados

Você pode definir um escopo de pesquisa escolhendo o botão **escolher pastas de pesquisa** (é semelhante a **...**) ao lado da caixa **examinar** . Na caixa de diálogo **Escolher Pastas de Pesquisa**, especifique um conjunto de pastas a ser pesquisado e salve a especificação para reutilizá-la mais tarde.

> [!TIP]
> Se você mapeou a unidade de um computador remoto para o computador local, especifique as pastas a serem pesquisadas no computador remoto.

### <a name="create-custom-component-sets"></a>Criar conjuntos de componentes personalizados

Você pode definir conjuntos de componentes como o escopo da pesquisa escolhendo o botão **Editar conjunto de componentes personalizados** ao lado da caixa **Examinar**. Você pode especificar os componentes .NET ou COM instalados, projetos do Visual Studio incluídos em sua solução ou qualquer biblioteca de tipos ou assembly (*. dll*, *. tlb*, *. olb*, *. exe* ou *. ocx*). Para pesquisar referências, selecione a caixa **Examinar referências**.

## <a name="multi-caret-selection"></a>Seleção de vários cursores

> [!NOTE]
> Esta seção aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Seleção de bloco](/visualstudio/mac/block-selection).

**Introduzido no Visual Studio 2017 versão 15.8**

Use a *seleção de vários cursores* para fazer a mesma edição em dois ou mais locais ao mesmo tempo. Por exemplo, você pode inserir o mesmo texto ou modificar o texto existente em vários locais ao mesmo tempo.

Na captura de tela a seguir, `-0000` está selecionado em três locais. Se o usuário pressionar **Excluir**, as três seleções serão excluídas:

![Seleção de vários cursores em um arquivo XML no Visual Studio](media/multi-caret-selection.png)

Para selecionar vários cursores, clique ou faça a primeira seleção de texto como de costume e, em seguida, pressione **Alt** enquanto você clica ou seleciona o texto em cada local adicional. Você pode adicionar texto correspondente automaticamente como seleções adicionais ou selecionar uma caixa de texto para editar de modo idêntico em cada linha.

> [!TIP]
> Se você tiver selecionado **Alt** como a tecla modificadora do clique do mouse Ir para Definição em **Ferramentas** > **Opções**, a seleção de vários cursores estará desabilitada.

### <a name="commands"></a>Comandos

Use as seguintes teclas e ações para os comportamentos da seleção de vários cursores:

|Atalho|Ação|
|-|-|
|**Ctrl** + **ALT** + clique|Adicionar um cursor secundário|
|**Ctrl** + **ALT** + clique duas vezes|Adicionar uma seleção de palavra secundária|
|**Ctrl** + **ALT** + Clique + arrastar|Adicionar uma seleção secundária|
|**Shift** + **ALT** + **.**|Adicionar o próximo texto correspondente como uma seleção|
|**Shift** + **ALT** + **;**|Adicionar todo o texto correspondente como seleções|
|**Shift** + **ALT** + **,**|Remover a última ocorrência selecionada|
|**Shift** + **ALT**+**/**|Ignorar a próxima ocorrência de correspondência|
|**ALT** + clique|Adicionar uma seleção de caixa|
|**Esc** ou clique|Limpar todas as seleções|

Alguns dos comandos também estão disponíveis no menu **Editar**, em **Vários Cursores**:

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Captura de tela do menu suspenso de múltiplos Cursors no Visual Studio":::

## <a name="see-also"></a>Confira também

- [Usar expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refatorar um código no Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Seleção de bloco (Visual Studio para Mac)](/visualstudio/mac/block-selection)
