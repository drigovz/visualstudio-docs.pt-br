---
title: Depurar um controle WebView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69c7aa5e83da4ec829b439940d4affcd536bc128
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922957"
---
# <a name="debug-a-webview-control"></a>Depurar um controle do WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows e Windows Phone] (... /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Para inspecionar e depurar os controles do `WebView` em um aplicativo do Tempo de Execução do Windows, você pode configurar o Visual Studio para anexar o Depurador de Scripts quando iniciar seu aplicativo. No Visual Studio 2013 Update 2, você tem duas formas de interagir com os controles do `WebView` usando o depurador:  
  
-   Abra o [Explorador do DOM](../debugger/quickstart-debug-html-and-css.md) para uma instância do `WebView` e inspecione os elementos de DOM, investigue os problemas de estilo de CSS e teste dinamicamente as mudanças renderizadas nos estilos.  
  
-   Selecione a página da Web ou o `iFrame` exibido na instância `WebView` como alvo na janela [Console do JavaScript](../debugger/javascript-console-commands.md), em seguida, interaja com a página da Web usando os comandos do console. O console dá acesso ao contexto de execução do script atual.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Anexar o depurador (C#, Visual Basic, C++)  
  
1.  No Visual Studio, adicione um controle `WebView` ao seu aplicativo de Tempo de Execução do Windows.  
  
2.  No Gerenciador de Soluções, abra as propriedades do projeto, escolhendo **Propriedades** do menu de atalho do projeto.  
  
3.  Escolha **Depurar**. Na lista **Processo do aplicativo**, escolha **Script**.  
  
     ![Anexar o depurador de script](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Opcional) Para versões de não Express do Visual Studio, desabilitar a depuração de just-in-time (JIT) escolhendo **ferramentas**, **opções**, **depuração**, **Just-In-Time**, e, em seguida, desabilite a depuração JIT para Script.  
  
    > [!NOTE]
    >  Desabilitando a depuração JIT, você pode ocultar caixas de diálogo para exceções não tratadas que ocorrem em algumas páginas da Web. No Visual Studio Express, a depuração JIT sempre fica desabilitada.  
  
5.  Pressione F5 para iniciar a depuração.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Use o Explorador do DOM para inspecionar e depurar um controle WebView  
  
1.  (C#, Visual Basic, C++) Anexe o depurador do script ao seu aplicativo. Veja a primeira seção para obter instruções.  
  
2.  Se ainda não o fez, adicione um controle `WebView` ao seu aplicativo e pressione F5 para iniciar a depuração.  
  
3.  Navegue até a página que contém os controles `Webview`.  
  
4.  Abra a janela do Explorador do DOM do controle `WebView` escolhendo **Depuração**, **Windows**, **Explorador do DOM** e escolha a URL do `WebView` que deseja inspecionar.  
  
     ![Abrir o Explorador do DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     O Explorador do DOM associado ao `WebView` aparece como uma nova guia no Visual Studio.  
  
5.  Exibir e modificar elementos de DOM ativos e estilos CSS, conforme descrito em [estilos de CSS depurar usando o Explorador do DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usar a janela Console do JavaScript para inspecionar e depurar um controle WebView  
  
1.  (C#, Visual Basic, C++) Anexe o depurador do script ao seu aplicativo. Veja a primeira seção para obter instruções.  
  
2.  Se ainda não o fez, adicione um controle `WebView` ao seu aplicativo e pressione F5 para iniciar a depuração.  
  
3.  Abra a janela Console do JavaScript para o controle `WebView` escolhendo **Depurar**, **Windows**, **Console do JavaScript**.  
  
     A janela Console do JavaScript aparece.  
  
4.  Navegue até a página que contém os controles `Webview`.  
  
5.  Na janela Console, selecione a página da Web ou um `iFrame` exibido pelo controle `WebView` na lista **Destino**.  
  
     ![Destino de seleção na janela do console JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Usando o console, você pode interagir com um único `WebView`, `iFrame`, compartilhar o contrato ou web worker por vez. Cada elemento requer uma instância separada do host da plataforma web (WWAHost.exe). Você pode interagir com um host por vez.  
  
6.  Exibir e modificar variáveis no seu aplicativo ou usar comandos do console, conforme descrito em [guia de início rápido: Depurar o JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) e [comandos do JavaScript Console](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Consulte também  
 [Início Rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
