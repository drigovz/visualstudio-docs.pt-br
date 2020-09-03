---
title: Localizar e substituir em arquivos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dddd55714e53516ba1ccd8a11c99761a4db7136a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585620"
---
# <a name="replace-in-files"></a>Substituir em Arquivos

**Substituir nos Arquivos** permite pesquisar o código de um conjunto especificado de arquivos para uma cadeia de caracteres ou expressão e alterar algumas ou todas as correspondências encontradas. As correspondências encontradas e as ações executadas são listadas na janela **Localizar resultados** selecionada em **Opções de resultado**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes daqueles descritos na **ajuda** , dependendo de suas configurações ativas ou edição. Para alterar as configurações, por exemplo, para configurações **Gerais** ou do **Visual C++**, escolha **Ferramentas** > **Importar e Exportar Configurações** e, em seguida, escolha **Redefinir todas as configurações**.

É possível usar qualquer um dos métodos a seguir para exibir **Substituir nos Arquivos** na janela **Localizar e Substituir**.

## <a name="to-display-replace-in-files"></a>Para exibir Substituir nos Arquivos

1. No menu **Editar**, expanda **Localizar e Substituir**.

2. Escolha **Substituir nos Arquivos**.

   — ou —

   Se a janela **Localizar e Substituir** ainda estiver aberta, na barra de ferramentas, escolha **Substituir nos Arquivos**.

## <a name="find-what"></a>Localizar

Para pesquisar uma nova cadeia de caracteres de texto ou expressão, especifique-a na caixa. Para pesquisar qualquer uma das 20 cadeias de caracteres mais pesquisadas recentemente, abra a lista suspensa e escolha a cadeia de caracteres. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de pesquisa. Para obter mais informações, confira [Usar expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> O botão **Construtor de Expressões** só será habilitado se você tiver selecionado **Usar Expressões Regulares** em **Encontrar Opções**.

## <a name="replace-with"></a>Substitua por

Para substituir instâncias da cadeia de caracteres na caixa **Localizar** por outra cadeia de caracteres, digite a cadeia de caracteres de substituição na caixa **Substituir por**. Para excluir instâncias da cadeia de caracteres na caixa **O que localizar**, deixe esse campo em branco. Abra a lista para exibir as 20 cadeias de caracteres que você pesquisou mais recentemente. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de substituição. Para obter mais informações, confira [Usar expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Examinar

A opção escolhida na lista suspensa **Examinar** determina se a opção **Substituir nos Arquivos** só pesquisará em arquivos ativos ou em todos os arquivos armazenados em determinadas pastas. Selecione um escopo da pesquisa na lista, digite um caminho de pasta ou clique no botão **Procurar (...) ** para exibir a caixa de diálogo **Escolher Pastas de Pesquisa** e escolha um conjunto de pastas a pesquisar. Também é possível digitar um caminho diretamente na caixa **Examinar**.

> [!NOTE]
> Se a opção **Examinar** selecionada fizer com que você pesquise um arquivo do qual você fez check-out do controle do código-fonte, apenas a versão desse arquivo que tiver sido baixada em seu computador local será pesquisada.

## <a name="find-options"></a>Opções de busca

Você pode expandir ou recolher a seção de **Opções de localização** . As opções a seguir podem ser marcadas ou desmarcadas:

**Diferenciar maiúsculas de minúsculas**

Quando selecionada, as janelas **Localizar Resultados** só exibem instâncias da cadeia de caracteres **Localizar** que coincidam tanto em termos de conteúdo quanto de maiúsculas e minúsculas. Por exemplo, uma pesquisa por "MyObject" com **Coincidir com maiúsculas e minúsculas** selecionado retornará "MyObject", mas não "myobject" nem "MYOBJECT".

**Coincidir palavra inteira**

Quando selecionada, as janelas **Localizar Resultados** só exibirão instâncias da cadeia de caracteres **O que localizar** que coincidam em palavras inteiras. Por exemplo, uma pesquisa por "MyObject" retornará "MyObject", mas não "CMyObject" nem "MyObjectC".

**Usar expressões regulares**

Quando essa caixa de seleção está marcada, é possível usar notações especiais para definir padrões de texto nas caixas de texto **Localizar** ou **Substituir por**. Para obter uma lista dessas notações, confira [Usar expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Pesquisar nestes tipos de arquivo**

Essa lista indica os tipos de arquivos a serem pesquisados nos diretórios **Examinar**. Se esse campo for deixado em branco, todos os arquivos nos diretórios **Examinar** serão pesquisados. Selecione qualquer item na lista para inserir uma cadeia de caracteres de pesquisa pré-configurada que localizará arquivos desses tipos específicos.

## <a name="result-options"></a>Opções de resultado

Você pode expandir ou recolher a seção de **Opções de resultado** . As opções a seguir podem ser marcadas ou desmarcadas:

Janela **Localizar resultados 1**

Quando selecionada, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar Resultados 1**. Essa janela será aberta automaticamente para exibir seus resultados de pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 1**.

Janela **Localizar resultados 2**

Quando selecionada, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar Resultados 2**. Essa janela será aberta automaticamente para exibir seus resultados de pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 2**.

**Exibir somente nomes de arquivo**

Quando essa caixa de seleção estiver marcada, as janelas **Localizar Resultados** listarão os nomes e os caminhos completos para todos os arquivos que contenham a cadeia de caracteres de pesquisa. No entanto, os resultados não incluirão a linha de código na qual a cadeia de caracteres é exibida. Essa caixa de seleção está disponível somente para **Localizar em Arquivos**.

**Manter arquivos modificados abertos após Substituir Tudo**

Quando selecionada, essa opção deixa abertos todos os arquivos em que foram feitas substituições, para você poder desfazer ou salvar as alterações. Restrições de memória podem limitar o número de arquivos que podem permanecer abertos após uma operação de substituição.

> [!CAUTION]
> Você só pode usar o comando **Desfazer** em arquivos que permaneçam abertos para edição. Se essa opção não for selecionada, os arquivos que ainda não estiverem abertos para edição continuarão fechados e nenhuma opção **Desfazer** ficará disponível para eles.

## <a name="see-also"></a>Confira também

- [Localizar e substituir texto](../ide/finding-and-replacing-text.md)
- [Localizar nos arquivos](../ide/find-in-files.md)
- [Comandos do Visual Studio](../ide/reference/visual-studio-commands.md)
