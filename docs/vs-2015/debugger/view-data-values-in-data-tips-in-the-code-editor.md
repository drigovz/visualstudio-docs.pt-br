---
title: Exibir valores de dados em dicas de dados no editor de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700103"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Exibir valores de dados em Dicas de Dados no editor de códigos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os DataTips fornecem um modo conveniente de exibir informações sobre variáveis em seu programa durante a depuração. Os DataTips funcionam apenas no modo de interrupção e apenas com variáveis que estejam no escopo de execução atual.  
  
 No [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , os DataTips podem ser fixados em um local específico em um arquivo de origem ou podem flutuar sobre todas as [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] janelas.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Para exibir um DataTip (somente no modo de interrupção)  
  
1. Em uma janela de origem, coloque o ponteiro do mouse sobre qualquer variável no escopo atual.  
  
    Um DataTip aparece.  
  
   > [!NOTE]
   > Os DataTips são sempre avaliados no contexto onde a execução é suspensa e não por onde o cursor está passando. Se você passar o mouse sobre uma variável em outra função com o mesmo nome de uma variável que está no contexto atual, o valor da variável na outra função será exibido como o valor da variável no contexto atual.  
  
2. O DataTip desaparecerá quando você remover o ponteiro do mouse. Para fixar o DataTip para que ele permaneça aberto, clique no ícone **fixar na fonte** ou  
  
   - Clique com o botão direito do mouse em uma variável e clique em **fixar na origem**.  
  
     O DataTip fixado é fechado quando a sessão de depuração termina.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Para desafixar um DataTip e fazê-lo flutuar  
  
- Em um DataTip fixado, clique no ícone **Desafixar da origem** .  
  
     O ícone de fixar é alterado para a posição desafixada. O DataTip agora flutua sobre todas as janelas abertas. O DataTip flutuante é fechado quando a sessão de depuração termina.  
  
### <a name="to-repin-a-floating-datatip"></a>Ao refixar um DataTip flutuante  
  
- Em um DataTip, clique no ícone de fixar.  
  
     O ícone de fixar é alterado para a posição fixada. Se o DataTip estiver fora de uma janela de origem, o ícone de fixar estará desabilitado e o DataTip não poderá ser fixado.  
  
### <a name="to-close-a-datatip"></a>Para fechar um DataTip  
  
- Coloque o ponteiro do mouse sobre um DataTip e clique no ícone **fechar** .  
  
### <a name="to-close-all-datatips"></a>Para fechar todos os DataTips  
  
- No menu **depurar** , clique em **limpar todas as dicas**de data.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Para fechar todos os DataTips para um arquivo específico  
  
- No menu **depurar** , clique em **limpar todos os DataTips fixados em** *arquivo*.  
  
## <a name="expanding-and-editing-information"></a>Expandindo e editando as informações  
 Você pode usar os DataTips para expandir uma matriz, uma estrutura ou um objeto para exibir seus membros. Você também pode editar o valor de uma variável de um DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Para expandir uma variável para ver seus elementos  
  
- Em um DataTip, coloque o ponteiro do mouse sobre o **+** sinal que vem antes do nome da variável.  
  
     A variável expande para mostrar seus elementos na forma da árvore.  
  
     Quando a variável é expandida, você poderá usar as teclas de direção no teclado para mover para cima e para baixo. Outra opção é usar o mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Para editar o valor de uma variável usando um DataTip  
  
1. Em um DataTip, clique no valor. Isso está desabilitado para valores somente leitura.  
  
2. Digite um novo valor e pressione ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Criando um DataTip transparente  
 Se quiser ver o código que está por trás de um DataTip, poderá criar o DataTip temporariamente transparente. Isso não se aplica a DataTips fixados ou flutuantes.  
  
#### <a name="to-make-a-datatip-transparent"></a>Para criar um DataTip transparente  
  
- Em um DataTip, pressione CTRL.  
  
     O DataTip permanecerá transparente enquanto você mantiver pressionada a tecla CTRL.  
  
## <a name="visualizing-complex-data-types"></a>Visualizando tipos de dados complexos  
 Se um ícone de lupa aparecer ao lado de um nome de variável em um DataTip, um ou mais [visualizadores de criação personalizados](../debugger/create-custom-visualizers-of-data.md) estarão disponíveis para variáveis desse tipo de dados. Você pode usar um visualizador para exibir informações de uma maneira mais significativa, geralmente gráfica.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Para exibir o conteúdo de uma variável usando um visualizador  
  
- Clique no ícone de lupa para selecionar o visualizador padrão para o tipo de dados.  
  
     - ou -  
  
     Clique na seta do menu suspenso ao lado do visualizador para selecionar de uma lista de visualizadores apropriados para o tipo de dados.  
  
     Um visualizador exibe as informações.  
  
## <a name="adding-information-to-a-watch-window"></a>Adicionando informações a uma janela Inspeção  
 Se você quiser continuar a observar uma variável, poderá adicionar a variável à janela de **inspeção** de um DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Para adicionar uma variável à janela Inspeção  
  
- Clique com o botão direito do mouse em um DataTip e clique em **Adicionar inspeção**.  
  
     A variável é adicionada à janela **Watch** . Se você estiver usando uma edição que dá suporte a várias janelas de **inspeção** , a variável será adicionada ao **relógio 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importando e exportando DataTips  
 Você pode exportar DataTips para um arquivo XML, que pode ser compartilhado com um colega ou editado por um editor de texto.  
  
#### <a name="to-export-datatips"></a>Para exportar DataTips  
  
1. No menu Depurar, clique em **Exportar DataTips**.  
  
     A caixa de diálogo **Exportar DataTips** é exibida.  
  
2. Use técnicas de arquivo padrão para navegar até o local onde você deseja salvar o arquivo XML, digite um nome para o arquivo na caixa **nome do arquivo** e clique em **OK**.  
  
#### <a name="to-import-datatips"></a>Para importar DataTips  
  
1. No menu Depurar, clique em **importar DataTips**.  
  
     A caixa de diálogo **importar DataTips** é exibida.  
  
2. Use a caixa de diálogo para localizar o arquivo XML que você deseja abrir e clique em **OK**.  
  
## <a name="see-also"></a>Consulte Também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Como: usar a caixa de diálogo QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Como alterar o formato numérico das janelas do depurador](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
