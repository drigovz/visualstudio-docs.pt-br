---
title: Depurar estilos CSS usando o explorador do DOM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- CSS styles [Windows Store apps], debugging
- CSS rules [Windows Store apps], debugging
- CSS debugging [Windows Store apps]
- debugging, CSS rules [Windows Store apps]
- HTML debugging [Windows Store apps]
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 676a4ef2570873998f3ebc890e06d6d5ccae4cf2
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852431"
---
# <a name="debug-css-styles-using-dom-explorer"></a>Depurar estilos CSS com o Explorador do DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows e Windows Phone] (.. /Imagem/windows_and_phone_content. png "windows_and_phone_content")  
  
 Quando estiver Depurando aplicativos da Windows Store, Windows Phone aplicativos da loja e aplicativos criados usando Ferramentas do Visual Studio para Apache Cordova, você poderá exibir e alterar as regras de CSS para elementos DOM selecionados e seus elementos filho.  
  
 As guias **estilos** e **computado** no explorador do dom mostram as regras de CSS que se aplicam a um elemento selecionado. As regras são exibidas na ordem de sua especificidade de acordo com as regras de precedência de CSS. As regras na parte superior de um seletor ou estilo em uma guia (as regras mais específicas) serão as últimas a serem aplicadas ao elemento selecionado, e as regras na parte inferior de um seletor ou estilo serão as primeiras a serem aplicadas. Quando as regras são aplicadas, elas substituem as regras aplicadas anteriormente.  
  
 As guias **estilos**, **computado**e **alterações** fornecem exibições diferentes das informações de estilo.  
  
- Use a guia **estilos** para exibir as regras organizadas por nome do seletor de CSS, como `html, body`. Você também pode usar essa guia para habilitar ou desabilitar estilos específicos, editar valores manualmente e ver os resultados imediatos dessas alterações.  
  
- Use a guia **computada** para exibir os valores computados de um estilo. Por exemplo, se você definir um tamanho como 1em, o valor calculado pelo Internet Explorer poderá ser 16px. Os estilos nessa guia estão organizados por nome de estilo, como `height`. Você também pode usar essa guia para habilitar ou desabilitar estilos específicos, editar valores manualmente e ver os resultados imediatos dessas alterações.  
  
    > [!NOTE]
    > No Visual Studio 2013 atualização 2, as informações fornecidas na guia **rastreamento** foram mescladas com a guia **computada** e a guia **rastreamento** foi removida.  
  
- Use a guia **alterações** (somente para aplicativos da Windows Store e da Windows Phone Store) para identificar e rastrear os estilos CSS que você alterou durante uma sessão de depuração.  
  
> [!TIP]
> As alterações feitas aos estilos nas guias **estilos** e **computado** não são permanentes. Elas são perdidas quando você interrompe a depuração. Para alterar o código-fonte e recarregar as páginas sem parar e reiniciar o depurador, atualize seu aplicativo usando o botão de ![botão Atualizar aplicativo do Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Atualizar aplicativo**do Windows) na barra de ferramentas de **depuração** (somente aplicativos da Windows Store e da Windows Phone Store). Para obter mais informações, consulte [atualizar um aplicativo (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>Exemplo de correção de uma regra de CSS  
 Este exemplo mostra como inspecionar regras de CSS e depurar um problema de estilo. Por exemplo, vamos supor que você mude a cor de uma fonte usada para exibir títulos de grupo no modelo de [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Aplicativo de Separação.  
  
> [!NOTE]
> Este exemplo mostra um aplicativo da Windows Store, mas todos os recursos do explorador do DOM mostrados também se aplicam a um aplicativo da Windows Phone Store e, exceto para a guia alterações, um aplicativo criado usando Ferramentas do Visual Studio para Apache Cordova.  
  
#### <a name="to-view-and-change-css-rules"></a>Para exibir e alterar regras de CSS  
  
1. No Visual Studio, crie um novo aplicativo [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] usando JavaScript e HTML no modelo de projeto de Aplicativo de Separação.  
  
2. Em **Gerenciador de soluções**, abra Items. css. (Você pode encontrar o arquivo items.css na pasta de páginas.)  
  
3. Substitua o código de CSS a seguir:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
    }  
    ```  
  
     por este:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
        color: #ff6a00;  
    }  
    ```  
  
     Isso adiciona um estilo que especifica a cor #ff6a00 (laranja) para cada item na lista. O seletor de CSS, `.itemspage .itemslist .item`, indica um conjunto de nomes de classe para elementos DIV em items.html, que aparecem como elementos aninhados em DOM ativos. O elemento DIV `item` especifica os itens de lista.  
  
4. Selecione **simulador** na lista suspensa na barra de ferramentas **depurar** (**computador local** é o valor padrão).  
  
     ![Selecionar lista de destino de depuração](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5. Pressione F5 para executar seu aplicativo no modo de depuração.  
  
     Quando o aplicativo terminar o carregamento, examine os títulos dos itens de lista, como título do **Grupo: 1**. A cor não foi alterada. Assim, a tentativa de aplicar uma cor laranja aos títulos não funcionou. Vamos entender o que deu errado e corrigir usando as guias CSS no Explorador de DOMs.  
  
    > [!TIP]
    > Após o aplicativo ser exibido no Simulador, posicione o Simulador diretamente ao lado da janela do Visual Studio para verificar imediatamente os resultados de suas seleções e alterações nos estilos de CSS.  
  
6. Alterne para o Visual Studio e clique em **selecionar elemento** no explorador do dom (ou pressione CTRL + B). Isso altera o modo de seleção, permitindo que você selecione um item ao clicar nele, e traz o aplicativo para o primeiro plano. O modo é revertido após um único clique. Aqui está o botão **selecionar elemento** . ![Botão Selecionar elemento no explorador do DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
    > [!TIP]
    > Você também pode selecionar elementos HTML diretamente no Explorador de DOMs. Para obter mais informações sobre como selecionar elementos, consulte [início rápido: Depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7. No simulador, passe o mouse sobre o título do primeiro item na lista, **título do Grupo: 1**, no painel esquerdo da Home Page. O título é realçado, conforme mostrado aqui:  
  
     ![Usando o botão Selecionar elemento](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    > O Emulador do Windows Phone só permite destacar os elementos parcialmente ao focalizá-los.  
  
8. Clique no título destacado. O Explorador do DOM selecionará automaticamente o elemento HTML correspondente, semelhante a este.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Quando você seleciona o elemento H4 no Explorador do DOM, suas guias mostram as regras associadas ao elemento H4. A guia **computada** é mostrada aqui, com a propriedade `color` aberta:  
  
     ![Guia estilos de rastreamento no explorador do DOM](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Essa exibição fornece informações úteis sobre as regras que estão associadas ao estilo de `color`, como indicado a seguir:  
  
    - O seletor de CSS que alteramos no items.css, `.itemspage .itemslist .item`, não está sendo usado no cálculo de estilo final (aparece como texto tachado). Várias outras ocorrências do estilo de `color` também não estão sendo usadas.  
  
        > [!TIP]
        > No caso de nomes mais extensos do seletor, o nome completo aparece em uma dica de ferramenta.  
  
    - O valor computado de CSS final, `rgba(255, 255, 255, 0.87)`, é definido especialmente para o seguinte seletor de CSS: `.itemspage .itemslist .item .item-overlay .item-title`, que também é definido em items.css.  
  
        > [!TIP]
        > Agora que sabemos onde a cor do título está definida, também sabemos onde podemos alterá-la. No entanto, também podemos testar as alterações no Explorador do DOM sem atualizar o aplicativo, como mostrado nas etapas restantes.  
  
9. Desmarque a caixa de seleção da primeira ocorrência do estilo de `color`, que é para o seletor `.itemspage .itemslist .item .item-overlay .item-title`. Agora, no Simulador, você verá que a cor dos títulos dos itens mudará para laranja, como pretendíamos, e o seletor que modificamos no CSS, `.itemspage .itemslist .item`, não será mais substituído (isto é, não terá mais texto tachado aplicado). Aqui está a guia **calculada** depois de desmarcarmos a caixa de seleção.  
  
     ![A guia computada após a atualização do estilo CSS](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Selecione a guia **alterações** .  
  
     Use a guia **alterações** para identificar e rastrear as alterações de estilo feitas durante uma sessão de depuração. A ilustração a seguir mostra o seletor de `.itemspage .itemslist .item .item-overlay .item-title` na guia **alterações** , que agora é substituído.  
  
     ![Guia alterações do explorador do DOM](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. Você também pode editar manualmente os valores de estilo CSS e ver o resultado imediato usando a guia **estilos** .  
  
12. Selecione a guia **Estilos**.  
  
13. Abra o seletor de estilo de `.itemspage .itemslist .item .item-overlay .item-title`.  
  
14. Selecione a primeira ocorrência de estilo de `color` e clique duas vezes no valor da propriedade `rgb(255, 255, 255, 0.87)`.  
  
15. Use o teclado para modificar esse valor. Altere-o para `rgb(255, 255, 0, 0.87)` e pressione Enter. As cores dos títulos do item no Simulador mudam para amarelo.  
  
16. Para fazer alterações no arquivo CSS de origem, clique no link **itens. css** na guia **estilos** . Isso abre o Items. CSS, onde você pode alterar o valor do estilo de `color` no código do aplicativo. Para atualizar o aplicativo sem interromper e reiniciar o depurador, clique no botão ![Atualizar aplicativo do Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Atualizar aplicativo do Windows**) na barra de ferramentas **depurar** .  
  
## <a name="see-also"></a>Veja também  
 [Início rápido: Depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Depurar o layout usando o explorador do DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Exibir ouvintes de evento DOM](../debugger/view-dom-event-listeners.md)   
 [Suporte ao produto e acessibilidade](https://msdn.microsoft.com/library/tzbxw1af(VS.110).aspx)
