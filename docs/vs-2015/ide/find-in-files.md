---
title: Localizar em arquivos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655897"
---
# <a name="find-in-files"></a>Localizar em Arquivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O recurso Localizar nos Arquivos** permite pesquisar um conjunto especificado de arquivos. As correspondências encontradas e as ações executadas são listadas na janela **Localizar resultados** selecionada em **Opções de resultado**.

 É possível usar qualquer um dos métodos a seguir para exibir **Localizar nos Arquivos** na janela **Localizar e Substituir**.

### <a name="to-display-find-in-files"></a>Para exibir Localizar nos Arquivos

1. Na barra de menus, escolha **Editar**, **Localizar e Substituir**.

2. Escolha **Localizar nos Arquivos**.

   Para cancelar uma operação de localização, pressione CTRL + BREAK.

> [!NOTE]
> A ferramenta Localizar e Substituir não pesquisa diretórios com o conjunto de atributos `Hidden` ou `System`.

## <a name="find-what"></a>Localizar
 Para pesquisar uma nova cadeia de caracteres de texto ou expressão, especifique-a na caixa. Para pesquisar qualquer uma das 20 cadeias de caracteres mais pesquisadas recentemente, abra a lista e escolha a cadeia de caracteres que você deseja pesquisar. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de pesquisa. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Examinar
 A opção escolhida na lista suspensa **Examinar** determina se a opção **Localizar nos Arquivos** só pesquisará em arquivos ativos ou em todos os arquivos armazenados em determinadas pastas. Selecione um escopo da pesquisa na lista ou clique no botão **Procurar (...)** para exibir a caixa de diálogo **Escolher Pastas de Pesquisa** e insira seu próprio conjunto de diretórios. Também é possível digitar um caminho diretamente na caixa **Examinar**.

> [!WARNING]
> Com as opções **Solução Inteira** ou **Projeto Atual**, os arquivos de projeto e de solução não são pesquisados. Se você deseja examinar arquivos de projeto, escolha uma pasta de pesquisa.

> [!NOTE]
> Se a opção **Examinar** selecionada fizer com que você pesquise um arquivo do qual você fez check-out do controle do código-fonte, apenas a versão desse arquivo que tiver sido baixada em seu computador local será pesquisada.

## <a name="include-subfolders"></a>Incluir subpastas
 Especifica que as subpastas da pasta **Examinar** serão pesquisadas.

## <a name="find-options"></a>Opções de busca
 Você pode expandir ou recolher a seção de **Opções de localização** . As opções a seguir podem ser marcadas ou desmarcadas:

 Diferenciar maiúsculas de minúsculas quando selecionado, uma pesquisa de **Localizar resultados** diferenciará maiúsculas de minúsculas

 Corresponder palavra inteira quando selecionada, as janelas **Localizar resultados** só retornarão correspondências de palavras inteiras.

 Usar expressões regulares se essa caixa de seleção estiver marcada, você poderá usar notações especiais para definir padrões de texto para correspondência nas caixas de texto **Localizar** ou **substituir por** . Para obter uma lista dessas notações, consulte [usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Observe esses tipos de arquivo essa lista indica os tipos de arquivos a serem pesquisados nos diretórios de **procura** . Se esse campo estiver em branco, todos os arquivos nos diretórios **Examinar** serão pesquisados.

 Selecione qualquer item na lista para inserir uma cadeia de caracteres de pesquisa pré-configurada que localizará arquivos desses tipos específicos.

## <a name="result-options"></a>Opções de resultado
 Você pode expandir ou recolher a seção de **Opções de resultado** . As opções a seguir podem ser marcadas ou desmarcadas:

 Janela Localizar resultados 1 quando selecionado, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar resultados 1** . Essa janela será aberta automaticamente para exibir seus resultados de pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 1**.

 Janela Localizar resultados 2 quando selecionado, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar resultados 2** . Essa janela será aberta automaticamente para exibir seus resultados de pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 2**.

 Exibir nomes de arquivos exibe apenas uma lista de arquivos que contêm correspondências de pesquisa em vez de exibir as correspondências de pesquisa.

 O acréscimo de resultados acrescenta os resultados da pesquisa aos resultados da pesquisa anterior.

## <a name="see-also"></a>Consulte Também
 [Localizando e substituindo texto](../ide/finding-and-replacing-text.md) [substituir em arquivos de comandos do](../ide/replace-in-files.md) [Visual Studio](../ide/reference/visual-studio-commands.md)
