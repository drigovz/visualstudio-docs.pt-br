---
title: 'Início rápido: Depurar HTML e CSS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [Windows Store apps]
- DOM Explorer [Windows Store apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: 104
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be85bd5c09d59df576d66cef6cf2d4e7e34876ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687647"
---
# <a name="quickstart-debug-html-and-css"></a>Guia de início rápido: depurar HTML e CSS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows e Windows Phone] (.. /Imagem/windows_and_phone_content.png "windows_and_phone_content")  
  
 Para aplicativos JavaScript, o Visual Studio fornece uma experiência de depuração abrangente que inclui recursos que são familiares para desenvolvedores do Internet Explorer e do Visual Studio. Esses recursos têm suporte para o [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , Windows Phone aplicativos da loja e para aplicativos criados usando ferramentas do Visual Studio para Apache Cordova  
  
 Com o uso do modelo de depuração interativo fornecido pelas ferramentas de inspeção do DOM, você pode ver e modificar o código HTML e CSS renderizado. Você pode fazer tudo isso sem parar e reiniciar o depurador.  
  
 Neste tópico:  
  
- [Inspecionando o DOM ao vivo](#InspectingDOM)  
  
- [Selecionando elementos](#SelectingElements)  
  
  Para obter informações adicionais sobre o uso do Explorador do DOM, veja os tópicos a seguir:  
  
- [Depurar estilos CSS com o Explorador do DOM](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [Depurar o layout com o Explorador do DOM](../debugger/debug-layout-using-dom-explorer.md)  
  
- [Exibir os ouvintes de eventos do DOM](../debugger/view-dom-event-listeners.md)  
  
- [Atualizar um aplicativo (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [Depurar um controle do WebView](../debugger/debug-a-webview-control.md)  
  
  Para obter informações sobre outros recursos de depuração de JavaScript, como usar a janela do console do JavaScript e definir pontos de interrupção, consulte [início rápido: Depurar JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) e [depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="inspecting-the-live-dom"></a><a name="InspectingDOM"></a> Inspecionando o DOM ativo  
 O Explorador de DOMs mostra a página renderizada, e você pode usá-lo para alterar valores e imediatamente ver os resultados. Isso permite que você teste as mudanças sem parar e reiniciar o depurador. O código-fonte em seu projeto não muda quando você interage com a página usando esse método; então, quando você encontra as correções de código desejadas, você faz as mudanças no seu código-fonte.  
  
> [!TIP]
> Para impedir a interrupção e reinicialização do depurador quando você fizer mudanças no seu código-fonte, atualize seu aplicativo usando o botão **Atualizar aplicativo do Windows** na barra de ferramentas Depurar (ou pressionando F4). Para obter mais informações, consulte [atualizar um aplicativo (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 Você pode usar o Explorador de DOMs para:  
  
- Navegue pela subárvore de elementos do DOM e inspecione o código HTML, CSS e JavaScript renderizado.  
  
- Edite de forma dinâmica atributos e estilos CSS de elementos renderizados e veja os resultados imediatamente.  
  
- Inspecione como os estilos CSS foram aplicados aos elementos da página e rastreie as regras que foram aplicadas.  
  
  Ao depurar aplicativos, muitas vezes é preciso selecionar elementos no Explorador de DOMs. Quando você seleciona um elemento, os valores que aparecem nas guias à direita do Explorador do DOM são automaticamente atualizados para refletir o elemento selecionado no Explorador do DOM. Estas são as guias: **estilos**, **computado**, **layout**. Os aplicativos da Windows Store também dão suporte às guias **eventos** e **alterações** . Para obter mais informações sobre como selecionar elementos, confira [Selecionar elementos](#SelectingElements).  
  
> [!TIP]
> Se a janela Explorador do dom estiver fechada, escolha **depurar** > Explorador do**Windows**  >  **dom** para abri-lo novamente. A janela só aparece durante uma sessão de depuração de script.  
  
 No procedimento a seguir, avançaremos pelo processo de depurar interativamente um aplicativo usando o Explorador de DOMs. Vamos criar um aplicativo que usa um controle `FlipView` e depurá-lo. O aplicativo contém vários erros.  
  
> [!WARNING]
> O aplicativo de exemplo a seguir é um aplicativo da Windows Store. Os mesmos recursos têm suporte para Cordova, mas o aplicativo seria diferente.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Para depurar inspecionando o DOM ativo  
  
1. Crie uma nova solução no Visual Studio escolhendo **arquivo**  >  **novo projeto**.  
  
2. Escolha **JavaScript**  >  a**loja**do JavaScript, escolha **aplicativos do Windows** ou **Windows Phone aplicativos**e, em seguida, escolha **aplicativo em branco**.  
  
3. Digite um nome para o projeto, como `FlipViewApp` e escolha **OK** para criar o aplicativo.  
  
4. No elemento BODY de default.html, adicione este código:  
  
   ```html  
   <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
            style="display:none">  
       <div class="fixedItem" >  
           <img src="#" data-win-bind="src: flipImg" />  
       </div>  
   </div>  
   <div id="fView" style="width:100px;height:100px"  
       data-win-control="WinJS.UI.FlipView" data-win-options="{  
       itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
   </div>  
   ```  
  
5. Abra os arquivos default.css e adicione o seguinte CSS:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. Substitua o código em default.js por este código:  
  
   ```javascript  
   (function () {  
       "use strict";  
  
       var app = WinJS.Application;  
       var activation = Windows.ApplicationModel.Activation;  
  
       var myData = [];  
       for (var x = 0; x < 4; x++) {  
           myData[x] = { flipImg: "/images/logo.png" }  
       };  
  
       var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
       app.onactivated = function (args) {  
           if (args.detail.kind === activation.ActivationKind.launch) {  
               if (args.detail.previousExecutionState !==  
               activation.ApplicationExecutionState.terminated) {  
                   // TODO: . . .  
               } else {  
                   // TODO: . . .  
               }  
               args.setPromise(WinJS.UI.processAll());  
  
               updateImages();  
           }  
       };  
  
       function updateImages() {  
  
           pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
           pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
           pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
       };  
  
       app.oncheckpoint = function (args) {  
       };  
  
       app.start();  
  
       var publicMembers = {  
           items: pages  
       };  
  
       WinJS.Namespace.define("Data", publicMembers);  
  
   })();  
   ```  
  
    A ilustração a seguir mostra o que queremos ver se executarmos esse aplicativo no Emulador do Windows Phone (é similar no simulador). No entanto, para colocar o aplicativo nesse estado, teremos de corrigir uma série de bugs primeiro.  
  
    ![Aplicativo FlipView mostrando os resultados esperados](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. Escolha o **simulador** ou o **emulador 8,1 WVGA 4 polegadas 512 MB** na lista suspensa ao lado do botão **Iniciar Depuração** na barra de ferramentas **depurar** :  
  
    ![Selecionar lista de destino de depuração](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Escolha **depurar**  >  **Iniciar Depuração**ou pressione F5 para executar seu aplicativo no modo de depuração.  
  
    Isso executará o aplicativo no Simulador ou no Emulador do Windows Phone, mas você verá uma tela basicamente em branco porque o estilo contém alguns bugs. Uma primeira imagem `FlipView` aparecerá em um pequeno quadrado próximo ao meio da tela.  
  
9. Se você estiver executando o aplicativo no simulador, escolha o comando **alterar resolução** da barra de ferramentas à direita do simulador para configurar uma resolução de tela de 1280 x 800. Isso irá garantir que os valores mostrados nas tabelas a seguir correspondem ao que você vê no Simulador.  
  
10. Alterne para o Visual Studio e escolha a guia **Explorador do DOM**.  
  
    > [!TIP]
    > Você pode pressionar Alt+Tab ou F12 para alternar entre o Visual Studio e o aplicativo em execução.  
  
11. Na janela Explorador do DOM, selecione o elemento DIV correspondente à seção cuja ID é `"fView"`. Use as teclas de seta para exibir e selecionar o elemento DIV correto. (A tecla de seta para a direita permite que você exiba os filhos de um elemento.)  
  
     ![Explorador do DOM](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    > Você também pode selecionar o elemento DIV no canto inferior esquerdo da janela do console do JavaScript digitando `select(fView)` no prompt de entrada >> e, em seguida, pressionando ENTER.  
  
     Os valores que aparecem nas guias à direita da janela Explorador de DOMs são atualizados automaticamente para refletir o elemento atual no Explorador de DOMs.  
  
12. Escolha a guia **Calculado** à direita.  
  
     Essa guia mostra o valor calculado ou final de cada propriedade do elemento DOM selecionado.  
  
13. Abra a regra CSS de altura. Observe que há um estilo embutido definido como 100px, que aparece inconsistente com o valor da altura de 100% definido para o seletor de CSS `#fView` que está esmaecido. O texto tachado do seletor `#fView` indica que o estilo embutido está tendo precedência sobre esse estilo.  
  
     A ilustração a seguir mostra a guia **Computado**.  
  
     ![Guia calculada do explorador do DOM](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. Na janela principal do Explorador do DOM, clique duas vezes no estilo embutido para ver a altura e a largura do elemento DIV `fView`. Agora você pode editar os valores aqui. Nesse cenário, queremos removê-los completamente.  
  
15. Selecione `width: 100px;height: 100px;` e pressione as tecla Delete, em seguida, Enter. Depois que você pressiona Enter, os novos valores são imediatamente refletidos no Simulador ou no Emulador do Windows Phone, mesmo que você não tenha parado a sessão de depuração.  
  
    > [!IMPORTANT]
    > Assim como você pode atualizar atributos na janela do Explorador do DOM, também pode atualizar os valores exibidos nas guias **Estilos**, **Computado** e **Layout**. Para obter mais informações, consulte [depurar estilos CSS usando o explorador do dom](../debugger/debug-css-styles-using-dom-explorer.md) e o layout de [depuração usando o explorador do dom](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Alterne para o aplicativo selecionando o Simulador ou o Emulador do Windows Phone, ou usando as teclas Alt+Tab.  
  
     Agora o controle `FlipView` parece maior do que o tamanho da tela do Simulador ou do Emulador do Windows Phone. Esse não é o resultado esperado. Para investigar, retorne ao Visual Studio.  
  
17. No Explorador do DOM, selecione a guia **Calculado** novamente e abra a regra de altura. O elemento fView ainda mostrará o valor 100%, conforme esperado do CSS, mas o valor calculado será igual à altura da tela do Simulador (por exemplo, 800px ou 667.67px), que não é o que queremos para este aplicativo. Para investigar, você pode remover a altura e a largura do elemento DIV `fView`.  
  
18. Na guia **Estilos**, desmarque as propriedades de altura e largura para o seletor de CSS `#fView`.  
  
     A guia **Calculado** agora mostrará a altura de 400 px. As informações indicam que esse valor é proveniente do seletor .win-flipview especificado em ui-dark.css, que é um arquivo CSS da plataforma.  
  
19. Retorne ao aplicativo.  
  
     As coisas melhoraram. No entanto, ainda há um problema a ser corrigido: as margens parecem muito grandes.  
  
20. Para investigar, alterne para o Visual Studio e escolha a guia **layout** para examinar o modelo de caixa do elemento.  
  
     Na guia **layout** , você verá os seguintes valores:  
  
    - No caso do Simulador: 320 px (Deslocamento) e 320 px (Margem).  
  
    - No caso do Emulador do Windows Phone: 100 px (Deslocamento) e 100 px (Margem).  
  
      A ilustração a seguir mostra como a guia **layout** é exibida se você estiver usando o emulador de telefone (100px deslocamento e margem).  
  
      ![Guia de layout do explorador do DOM](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      Isso não parece estar correto. A guia **Calculado** também mostra os mesmos valores de margem.  
  
21. Escolha a guia **Estilos** e localize o seletor CSS `#fView`. Aqui, você vê um valor de 25% para a propriedade **margem**.  
  
22. Selecione o valor 25%, altere-o para 25px e pressione Enter.  
  
23. Também na guia **Estilos**, escolha a regra de altura do seletor .win-flipview, mude de 400 px para 500 px e pressione Enter.  
  
24. Retorne ao aplicativo e você verá que o posicionamento dos elementos parecerá correto. Para fazer correções na origem e atualizar o aplicativo sem interromper e reiniciar o depurador, consulte o procedimento a seguir.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Para atualizar o aplicativo durante a depuração  
  
1. Enquanto o aplicativo ainda está em execução, alterne para o Visual Studio.  
  
2. Abra o default.html e modifique o código-fonte alterando a altura e a largura do elemento DIV `"fView"` para 100%.  
  
3. Escolha o botão **Atualizar aplicativo do Windows** na barra de ferramentas Depurar (ou pressione F4). O botão tem a seguinte aparência: ![atualizar o botão do aplicativo do Windows](../debugger/media/js-refresh.png "JS_Refresh").  
  
     As páginas do aplicativo são recarregadas e o Simulador ou Emulador do Windows Phone volta para o primeiro plano.  
  
     Para obter mais informações sobre o recurso de atualização, consulte [atualizar um aplicativo (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="selecting-elements"></a><a name="SelectingElements"></a> Selecionando elementos  
 Você pode selecionar elementos DOM de três maneiras ao depurar um aplicativo:  
  
- Clicando diretamente nos elementos na janela Explorador de DOMs (ou usando as teclas de direção).  
  
- Usando o botão **Selecionar Elemento** (Ctrl+B).  
  
- Usando o `select` comando, que é um dos comandos do [console do JavaScript](../debugger/javascript-console-commands.md).  
  
  Quando você usa a janela Explorador de DOMs para selecionar elementos e posiciona o ponteiro do mouse em um elemento, o elemento correspondente é realçado no aplicativo em execução. Você deve clicar no elemento, no Explorador do DOM, para selecioná-lo ou pode usar as teclas de direção para realçar e selecionar elementos. Você também pode selecionar elementos no Explorador do DOM usando o botão **Selecionar elemento**. A ilustração a seguir mostra o botão **Selecionar Elemento**.  
  
  ![Botão Selecionar elemento no explorador do DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  Quando você clica em **Selecionar elemento** (ou pressiona Ctrl+B), isso altera o modo de seleção para que você possa selecionar um item no Explorador do DOM clicando nele no aplicativo em execução. O modo retorna à seleção normal após um único clique. Quando você clica em **Selecionar elemento**, o aplicativo vai para o primeiro plano e o cursor muda para refletir o novo modo de seleção. Quando você clica no elemento com o contorno, o Explorador de DOMs volta para o primeiro plano com o elemento especificado selecionado.  
  
  Antes de escolher **Selecionar Elemento**, você pode especificar se é para realçar os elementos no aplicativo em execução ativando/desativando o botão **Exibir realces de página da Web**. A ilustração a seguir mostra esse botão. Os realces são exibidos por padrão.  
  
  ![Exibir botão de destaques de página da Web](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Quando você escolhe realçar os elementos, os elementos que você focalizar no Simulador são realçados. As cores dos elementos realçados correspondem ao modelo de caixa que aparece na guia **Layout** do Explorador do DOM.  
  
> [!NOTE]
> Realçar elementos ao focalizá-los só tem suporte parcial no Emulador do Windows Phone.  
  
 Para obter um exemplo que demonstra como selecionar elementos usando o botão **selecionar elemento** , consulte [depurar estilos CSS usando o explorador do dom](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="browser-and-platform-support"></a><a name="BrowserSupport"></a> Suporte a navegadores e plataformas  
 As ferramentas do Visual Studio para JavaScript, o Explorador do DOM e a janela Console do JavaScript são suportadas nas seguintes plataformas:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] e aplicativos da Windows Phone Store que usam JavaScript e HTML  
  
- Internet Explorer 11 em execução no [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Internet Explorer 10 em execução no [!INCLUDE[win8](../includes/win8-md.md)]  
  
  Acesse [aqui](https://developer.microsoft.com/windows/downloads/sdk-archive) para baixar [!INCLUDE[win8](../includes/win8-md.md)] e Visual Studio.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Depurar estilos CSS usando o explorador do DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Depurar o layout usando o explorador do DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Exibir ouvintes de eventos DOM](../debugger/view-dom-event-listeners.md)   
 [Atualizar um aplicativo (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Depurar um controle WebView](../debugger/debug-a-webview-control.md)   
 [Atalhos de teclado](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Comandos do console do JavaScript](../debugger/javascript-console-commands.md)   
 [Depurar HTML, CSS e código de exemplo JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Suporte ao produto e acessibilidade](https://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)
