---
title: Substituir nos arquivos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669967"
---
# <a name="replace-in-files"></a>Substituir em Arquivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O recurso Substituir nos Arquivos** permite pesquisar o código de um conjunto especificado de arquivos em busca de uma cadeia de caracteres ou uma expressão e alterar algumas ou todas as correspondências encontradas. As correspondências encontradas e as ações executadas são listadas na janela **Localizar resultados** selecionada em **Opções de resultado**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 É possível usar qualquer um dos métodos a seguir para exibir **Substituir nos Arquivos** na janela **Localizar e Substituir**.

### <a name="to-display-replace-in-files"></a>Para exibir Substituir nos Arquivos

1. No menu **Editar**, expanda **Localizar e Substituir**.

2. Escolha **Substituir nos Arquivos**.

     — ou —

     Se a janela **Localizar e Substituir** ainda estiver aberta, na barra de ferramentas, escolha **Substituir nos Arquivos**.

## <a name="find-what"></a>Localizar
 Para pesquisar uma nova cadeia de caracteres de texto ou expressão, especifique-a na caixa. Para pesquisar qualquer uma das 20 cadeias de caracteres mais pesquisadas recentemente, abra a lista e escolha a cadeia de caracteres que você deseja pesquisar. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de pesquisa. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Substitua por
 Para substituir instâncias da cadeia de caracteres na caixa **Localizar** por outra cadeia de caracteres, digite a cadeia de caracteres de substituição na caixa **Substituir por**. Para excluir instâncias da cadeia de caracteres na caixa **O que localizar**, deixe esse campo em branco. Abra a lista para exibir as 20 cadeias de caracteres que você pesquisou mais recentemente. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de substituição. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Examinar
 A opção escolhida na lista suspensa **Examinar** determina se a opção **Substituir nos Arquivos** só pesquisará em arquivos ativos ou em todos os arquivos armazenados em determinadas pastas. Selecione um escopo da pesquisa na lista, digite um caminho de pasta ou clique no botão **Procurar (...) ** para exibir a caixa de diálogo **Escolher Pastas de Pesquisa** e escolha um conjunto de pastas a pesquisar. Também é possível digitar um caminho diretamente na caixa **Examinar**.

> [!NOTE]
> Se a opção **Examinar** selecionada fizer com que você pesquise um arquivo do qual você fez check-out do controle do código-fonte, apenas a versão desse arquivo que tiver sido baixada em seu computador local será pesquisada.

## <a name="find-options"></a>Opções de busca
 Você pode expandir ou recolher a seção de **Opções de localização** . As opções a seguir podem ser marcadas ou desmarcadas:

 Diferenciar maiúsculas de minúsculas quando selecionado, as janelas **Localizar resultados** só exibirão instâncias da cadeia de caracteres **Localizar** que correspondam por conteúdo e por caso. Por exemplo, uma pesquisa por "MyObject" com **Coincidir com maiúsculas e minúsculas** selecionado retornará "MyObject", mas não "myobject" nem "MYOBJECT".

 Coincidir palavra inteira quando selecionada, as janelas **Localizar resultados** só exibirão instâncias da cadeia de caracteres **Localizar** que correspondam em palavras completas. Por exemplo, uma pesquisa por "MyObject" retornará "MyObject", mas não "CMyObject" nem "MyObjectC".

 Usar expressões regulares quando essa caixa de seleção está marcada, você pode usar notações especiais para definir padrões de texto nas caixas de texto **Localizar** ou **substituir por** . Para obter uma lista dessas notações, consulte [usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Observe esses tipos de arquivo essa lista indica os tipos de arquivos a serem pesquisados nos diretórios de **procura** . Se esse campo for deixado em branco, todos os arquivos nos diretórios **Examinar** serão pesquisados.

 Selecione qualquer item na lista para inserir uma cadeia de caracteres de pesquisa pré-configurada que localizará arquivos desses tipos específicos.

## <a name="result-options"></a>Opções de resultado
 Você pode expandir ou recolher a seção de **Opções de resultado** . As opções a seguir podem ser marcadas ou desmarcadas:

 Janela Localizar resultados 1 quando selecionado, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar resultados 1** . Essa janela será aberta automaticamente para exibir seus resultados de pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 1**.

 Janela Localizar resultados 2 quando selecionado, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar resultados 2** . Essa janela será aberta automaticamente para exibir seus resultados de pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 2**.

 Exibir nomes de arquivos somente quando essa caixa de seleção está marcada, as janelas localizar resultados listam os nomes e caminhos completos de todos os arquivos que contêm a cadeia de caracteres de pesquisa. No entanto, os resultados não incluirão a linha de código na qual a cadeia de caracteres é exibida. Essa caixa de seleção só está disponível para Localizar em Arquivos.

 Manter arquivos modificados abertos depois de substituir tudo quando selecionado, deixa abrir todos os arquivos em que as substituições foram feitas, para que você possa desfazer ou salvar as alterações. Restrições de memória podem limitar o número de arquivos que podem permanecer abertos após uma operação de substituição.

> [!CAUTION]
> Você só pode usar o comando **Desfazer** em arquivos que permaneçam abertos para edição. Se essa opção não for selecionada, os arquivos que ainda não estiverem abertos para edição continuarão fechados e nenhuma opção **Desfazer** ficará disponível para eles.

## <a name="see-also"></a>Consulte Também
 [Localizando e substituindo o texto](../ide/finding-and-replacing-text.md) [Localizar em arquivos comandos do](../ide/find-in-files.md) [Visual Studio](../ide/reference/visual-studio-commands.md)
