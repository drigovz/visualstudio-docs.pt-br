---
title: Exibir valores de dados em DataTips no editor de códigos | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afb318c8aa327345b3cd76ee16b718db1e0386aa
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826723"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Exibir os valores de dados em DataTips no editor de códigos
Os DataTips fornecem um modo conveniente de exibir informações sobre variáveis em seu programa durante a depuração. Os DataTips funcionam apenas no modo de interrupção e apenas com variáveis que estejam no escopo de execução atual. Se essa for a primeira vez que você tentou depurar o código, você talvez queira ler [gravar melhor C# usando o Visual Studio de código](../debugger/write-better-code-with-visual-studio.md) e [depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md) antes de prosseguir com este artigo.
  
### <a name="to-display-a-datatip"></a>Para exibir um DataTip  
  
1. Defina um ponto de interrupção e iniciar a depuração (pressione **F5**).

2. Quando em pausa no depurador, coloque o ponteiro do mouse sobre qualquer variável no escopo atual.
  
     Um DataTip aparece.
  
3.  O DataTip desaparecerá quando você remover o ponteiro do mouse. Para fixar o DataTip de modo que ela permaneça aberta, clique o **fixar à origem** ícone ou o botão direito do mouse em uma variável, em seguida, clique em **fixar à origem**.

    ![A fixação de uma dica de dados](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > Os DataTips são sempre avaliados no contexto onde a execução é suspensa e não por onde o cursor está passando. Se você passar o mouse sobre uma variável em outra função com o mesmo nome de uma variável que está no contexto atual, o valor da variável na outra função será exibido como o valor da variável no contexto atual.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Para desafixar um DataTip e fazê-lo flutuar  
  
-   Em um DataTip fixado, clique o **Desafixar da origem** ícone.  
  
     O ícone de fixar é alterado para a posição desafixada. O DataTip agora flutua sobre todas as janelas abertas. O DataTip flutuante é fechado quando a sessão de depuração termina.  
  
### <a name="to-repin-a-floating-datatip"></a>Ao refixar um DataTip flutuante  
  
-   Em um DataTip, clique no ícone de fixar.  
  
     O ícone de fixar é alterado para a posição fixada. Se o DataTip estiver fora de uma janela de origem, o ícone de fixar estará desabilitado e o DataTip não poderá ser fixado.  
  
### <a name="to-close-a-datatip"></a>Para fechar um DataTip  
  
-   Coloque o ponteiro do mouse sobre um DataTip e, em seguida, clique no **fechar** ícone.  
  
### <a name="to-close-all-datatips"></a>Para fechar todos os DataTips  
  
-   Sobre o **Debug** menu, clique em **limpar todos os DataTips**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Para fechar todos os DataTips para um arquivo específico  
  
-   Sobre o **depurar** menu, clique em **limpar todos os DataTips fixados no** *arquivo*.  
  
## <a name="expand-and-edit-information"></a>Expandir e editar informações  
 Você pode usar os DataTips para expandir uma matriz, uma estrutura ou um objeto para exibir seus membros. Você também pode editar o valor de uma variável de um DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Para expandir uma variável para ver seus elementos  
  
-   Em um DataTip, coloque o ponteiro do mouse o **+** entrada que antecede o nome da variável.  
  
    A variável expande para mostrar seus elementos na forma da árvore.

    ![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "exibir uma dica de dados")
  
    Quando a variável é expandida, você poderá usar as teclas de direção no teclado para mover para cima e para baixo. Outra opção é usar o mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Para editar o valor de uma variável usando um DataTip  
  
1.  Em um DataTip, clique no valor. Isso está desabilitado para valores somente leitura.  
  
2.  Digite um novo valor e pressione ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Criando um DataTip transparente  
 Se quiser ver o código que está por trás de um DataTip, poderá criar o DataTip temporariamente transparente. Isso não se aplica a DataTips fixados ou flutuantes.  
  
#### <a name="to-make-a-datatip-transparent"></a>Para criar um DataTip transparente  
  
-   Em um DataTip, pressione CTRL.  
  
     O DataTip permanecerá transparente enquanto você mantiver pressionada a tecla CTRL.  
  
## <a name="visualize-complex-data-types"></a>Visualizar os tipos de dados complexos  
 Se um ícone de lupa aparecer ao lado de um nome de variável em um DataTip, um ou mais [visualizadores](../debugger/create-custom-visualizers-of-data.md), como o [visualizadores de cadeia de caracteres](../debugger/string-visualizer-dialog-box.md), estão disponíveis para variáveis desse tipo de dados. Você pode usar um visualizador para exibir informações de uma maneira mais significativa, geralmente gráfica.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Para exibir o conteúdo de uma variável usando um visualizador  
  
-   Clique no ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ícone do visualizador") para selecionar o visualizador padrão para o tipo de dados.  
  
     -ou-  
  
     Clique na seta do menu suspenso ao lado do visualizador para selecionar de uma lista de visualizadores apropriados para o tipo de dados.  
  
     Um visualizador exibe as informações.  
  
## <a name="add-information-to-a-watch-window"></a>Adicionar informações a uma janela Inspeção  
 Se você quiser continuar a inspecionar uma variável em uma exibição de lista, você pode adicionar a variável para o **inspeção** janela a partir de um DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Para adicionar uma variável à janela Inspeção  
  
-   Um DataTip com o botão direito e, em seguida, clique em **Adicionar inspeção**.  
  
     A variável é adicionada para o **inspeção** janela. Se você estiver usando uma edição que dá suporte a vários **Watch** windows, a variável é adicionada à **inspeção 1.**  
  
## <a name="import-and-export-datatips"></a>Importar e exportar DataTips  
 Você pode exportar DataTips para um arquivo XML, que pode ser compartilhado com um colega ou editado por um editor de texto.  
  
#### <a name="to-export-datatips"></a>Para exportar DataTips  
  
1.  No menu Depurar, clique em **exportar DataTips**.  
  
     O **exportar DataTips** caixa de diálogo é exibida.  
  
2.  Use técnicas de arquivo padrão para navegar até o local onde você deseja salvar o arquivo XML, digite um nome para o arquivo na **nome do arquivo** caixa e, em seguida, clique em **Okey**.  
  
#### <a name="to-import-datatips"></a>Para importar DataTips  
  
1.  No menu Depurar, clique em **importar DataTips**.  
  
     O **importar DataTips** caixa de diálogo é exibida.  
  
2.  Use a caixa de diálogo para localizar o arquivo XML que você deseja abrir e clique em **Okey**.  
  
## <a name="see-also"></a>Consulte também  
 [O que está sendo depurado?](../debugger/what-is-debugging.md)  
 [Gravar melhor C# o código usando o Visual Studio](../debugger/write-better-code-with-visual-studio.md)  
 [Introdução à depuração](../debugger/debugger-feature-tour.md) [exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Inspeção e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   