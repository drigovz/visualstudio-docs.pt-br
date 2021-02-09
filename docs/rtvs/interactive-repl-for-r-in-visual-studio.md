---
title: REPL interativo para R
description: Como usar o ambiente REPL interativo para R no Visual Studio, que é integrado às janelas do editor.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0355f1017bb661b4f72325fb74f60653f69cd182
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878169"
---
# <a name="work-with-the-r-interactive-window"></a>Trabalhar com a janela R Interativo

As RTVS (Ferramentas do R para Visual Studio) fornecem a janela R Interativo, também conhecida como janela **REPL** (Read-Evaluate-Print-Loop), na qual você pode inserir código R e ver os resultados imediatamente. Todos os módulos, sintaxe e variáveis, bem como o IntelliSense, estão disponíveis na janela interativa.

A janela interativa também está integrada às janelas regulares do editor R. Você pode selecionar código e pressionar **Ctrl** + **Enter**, ou clicar com o botão direito do mouse e selecionar **executar em interativo**, e o código será executado linha por linha na janela interativa como se você o tivesse digitado diretamente. Quando o cursor está em uma única linha em uma janela do editor, **Ctrl** + **Enter** envia essa linha para a janela interativa e move o cursor para a próxima linha. Dessa forma, você pode simplesmente pressionar **Ctrl** + **Enter** repetidamente para percorrer o código.

Para experimentar esses recursos, siga o passo a passo [Introdução ao R](getting-started-with-r.md), bem como as seções neste artigo. Os [Snippets de código](code-snippets-for-r.md) também funcionam na janela interativa como nas janelas do editor de R.

## <a name="overview-of-the-interactive-window"></a>Visão geral da Janela Interativa

Digitar código R válido e pressionar **Enter** no final da linha executa o código nessa linha:

```repl
> 3 + 3
[1] 6
```

Pressionar **Enter** em qualquer lugar em uma entrada de linha única também executa essa linha.

Todas as entradas e saídas anteriores da REPL são somente leitura e não podem ser alteradas. No entanto, você pode selecionar e copiar o texto da janela a qualquer momento e também colá-lo. O código colado é executado como se fosse inserido linha por linha.

Ou seja, quando você começa a digitar uma instrução e pressiona **Enter**, as RTVS sabem quando a instrução precisa ser continuada e entram no modo multilinhas com um prompt + à esquerda e o recuo apropriado. As RTVS também preenchem as chaves, os colchetes e os parênteses:

![Entrada de instrução de várias linhas na janela interativa](media/repl-multiline-entry.png)

Nesse modo de várias linhas, a tecla **Enter** executa o bloco de código somente quando posicionado no final do bloco, caso contrário insere uma nova linha. No entanto, você pode pressionar **Ctrl** + **Enter** em qualquer posição para executar esse bloco de código imediatamente.

### <a name="toolbar-commands"></a>Comandos da barra de ferramentas

Aqui está a janela interativa com sua barra de ferramentas:

![Janela interativa com barra de ferramentas](media/repl-window.png)

Os comandos da barra de ferramentas são os seguintes, a maioria deles tem equivalentes de teclado e também estão disponíveis nos menus de diretório de trabalho **ferramentas** de r  >   e **ferramentas de r**  >   (ou conforme observado):

| Botão | Comando | Combinação de teclas | Descrição |
| --- | --- | --- | --- |
| ![Botão Reiniciar](media/repl-toolbar-01-reset.png) | Redefinir | **Ctrl** + **Shift** + **F10** | Redefine a sessão de janela interativa, limpando todas as variáveis e o histórico. |
| ![Botão Limpar](media/repl-toolbar-02-clear.png) | Limpar | **Ctrl** + **L** | Limpa a saída mostrada na janela interativa. não afeta as variáveis de sessão nem o histórico. |
| ![Botões Histórico](media/repl-toolbar-03-history.png) | Comando Histórico anterior<br/>Comando Próximo histórico | **Para cima**, **Para baixo**<br/>**ALT** + Para **cima**, **ALT** + **para baixo** | Percorre o histórico, com alguns comportamentos de blocos de código de várias linhas. Consulte [Histórico](#history). |
| ![Botão Carregar workspace](media/repl-toolbar-04-load-workspace.png) | Carregar workspace | N/D | Carrega um workspace anterior salvo (consulte [Workspaces e sessões](#workspaces-and-sessions). |
| ![Botão Salvar workspace como](media/repl-toolbar-05-save-workspace-as.png)| Salvar workspace | N/D | Salva o estado atual da sessão como um workspace (consulte [Workspaces e sessões](#workspaces-and-sessions). |
| ![Botão Script R de origem](media/repl-toolbar-06-source-r-script.png) | Script R de origem | **Ctrl** + **Shift** + **S** | Chama `source` com o script R atualmente ativo no editor do Visual Studio, que executa o código.  Esse botão só aparece quando um arquivo R é aberto no editor do Visual Studio. |
| ![Botão Script R de origem com eco](media/repl-toolbar-07-source-r-script-with-echo.png) | Script R de Origem com Eco | **Ctrl** + **Shift** + **Insira** | Igual ao Script R de Origem, mas exibe o conteúdo do script na janela interativa. |
| ![Botão Interromper R](media/repl-toolbar-08-interrupt-r.png)| Interromper R | **Esc** | Interrompe qualquer código em execução na janela interativa, como o loop `while` na captura de tela mostra no início dessa seção. |
| ![Botão Anexar depurador](media/repl-toolbar-09b-attach-debugger.png)| Anexar Depurador | N/D | Também disponível usando o comando **debug**  >  **Attach to R interativo** . |
| ![Botão Definir diretório de trabalho para o local do arquivo de origem](media/repl-toolbar-10-set-working-directory-source.png)| Definir diretório de trabalho para o local do arquivo de origem | **Ctrl** + **Shift** + **E** | Define o diretório de trabalho para o último arquivo de origem carregado na janela interativa (usando `source`). Consulte [Diretório de trabalho](#working-directory). |
| ![Botão Definir diretório de trabalho para o local do projeto](media/repl-toolbar-11-set-working-directory-to-project.png) | Definir diretório de trabalho para o local do projeto | **Ctrl** + **Shift** + **P** | Define o diretório de trabalho para a raiz do projeto carregado atualmente no Visual Studio. Consulte [Diretório de trabalho](#working-directory). |
| (Campo de texto) | Selecionar Diretório de Trabalho | N/D | Campo de entrada direta para o diretório de trabalho. Consulte [Diretório de trabalho](#working-directory). |

## <a name="workspaces-and-sessions"></a>Workspaces e sessões

Executar o código na janela interativa cria um contexto em sua sessão atual. O contexto é composto de variáveis globais, definições de função, cargas de biblioteca e assim por diante. Esse contexto é chamado coletivamente de *workspace* e você pode salvar e carregar workspaces a qualquer momento.

Selecionar o botão **Salvar Workspace Como** ou usar os prompts de comando **Ferramentas do R** > **Sessão** > **Salvar Workspace Como** solicitará um local e um nome de arquivo (a extensão padrão é *.RData*).

Para salvar um workspace usando um nome de arquivo específico (o padrão é *.RData*), clique no botão **Salvar Workspace** na REPL:

Para recarregar um workspace salvo anteriormente, selecione o botão **Carregar Workspace** ou use **Ferramentas do R** > **Sessão** > **Carregar Workspace** e navegue até o arquivo de workspace.

O botão **Redefinir** ou **Ferramentas do R** > **Sessão** > **Redefinir** limpa o contexto da sessão. Se você estiver usando uma sessão remota, a redefinição também excluirá o perfil do usuário no computador remoto para limpar todos os arquivos armazenados ali. (Consulte [Workspaces](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Diretório de trabalho

Normalmente, os desenvolvedores desejam alterar seu diretório de trabalho enquanto estão em uma sessão interativa. Vários comandos, disponíveis na barra de ferramentas, o menu do diretório de trabalho das **Ferramentas do R**  >   e o menu de contexto do projeto permitem que você defina facilmente um diretório de trabalho para o local de um arquivo de origem, o local ou o projeto ou qualquer outro local arbitrário. Isso ajuda a evitar a digitação de nomes de caminho completos ou de nomes de caminho relativos longos ao fazer referência a arquivos.

## <a name="history"></a>Histórico

Cada linha que você insere na janela interativa, incluindo as linhas enviadas de um editor, são mantidas no histórico da REPL. Você pode navegar pelo histórico com as teclas de seta Para Cima e Para Baixo, como provavelmente já está acostumado na linha de comando.

Uma diferença é que, se você começar a digitar na linha atual e pressionar Para Cima, essa linha atual será preservada no histórico, mesmo que ela ainda não tenha sido executada.

O histórico na janela interativa também funciona de forma inteligente com instruções de outro bloco de código que abrangem linhas. Ao percorrer o histórico com as teclas de seta Para Cima e Para Baixo, os blocos de código de várias linhas são recuperados como um todo e mostrados como a entrada atual. Neste ponto, as teclas de seta navegam por esse bloco de código linha por linha, até a parte superior ou inferior seja atingida. Na parte superior do bloco de código, a seta para cima recupera o item anterior no histórico; na linha inferior, a seta para baixo recupera o próximo item.

Esse comportamento acomoda o caso típico de executar novamente o último item no histórico com uma seta para cima e **digitar** a combinação de teclas, embora, naturalmente, permita a edição de um bloco de código de várias linhas pressionando a seta para cima para navegar até ele.

Para evitar a navegação em blocos de código de várias linhas, use os botões da barra de ferramentas ou **ALT +** +   - **seta para baixo e ALT para baixo**, e todos esses blocos são tratados como uma única linha.

A maneira mais fácil de experimentar os recursos de histórico é testá-los por contra própria na janela interativa. O código a seguir fornece várias instruções adequadas de linha única e de várias linhas. Use copiar e colar com cada instrução individualmente para criar o histórico apropriado. (Você também pode colar o código em um arquivo de código separado e, em seguida, enviar as linhas para a janela interativa com **Ctrl** + **Insira**.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```