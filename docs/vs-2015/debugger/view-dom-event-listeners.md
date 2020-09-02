---
title: Exibir ouvintes de eventos DOM | Microsoft Docs
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693585"
---
# <a name="view-dom-event-listeners"></a>Exibir os ouvintes de eventos do DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows e Windows Phone] (.. /Imagem/windows_and_phone_content.png "windows_and_phone_content")

 A guia **eventos** do explorador do dom mostra os eventos associados a um elemento DOM. Cada nó superior na guia **eventos** representa um evento que tem assinantes ativos. O nó superior contém subnós que representam os ouvintes registrados do evento específico. Além de exibir os ouvintes de eventos, você pode usar essa guia para navegar até o local do ouvinte de eventos no código JavaScript. As informações contidas neste tópico se aplicam a aplicativos da Windows Store que usam HTML e JavaScript.

 A lista na guia **eventos** é dinâmica. Se você adicionar um ouvinte de evento enquanto o aplicativo está em execução, o novo ouvinte de evento será exibido lá. Para obter informações sobre como adicionar e remover ouvintes de eventos, consulte [dicas para resolver problemas com ouvintes de eventos](#Tips) neste tópico.

> [!NOTE]
> Ouvintes de eventos para elementos de código que não são elementos DOM, como `xhr` , não aparecem na guia **eventos** .

## <a name="view-event-listeners-for-dom-elements"></a>Visualizar ouvintes de evento para elementos DOM
 Este exemplo mostra um aplicativo da Windows Phone Store. O recurso Explorador do DOM descrito aqui também tem suporte para aplicativos da Windows Store.

#### <a name="to-view-event-listeners"></a>Para exibir os ouvintes de eventos

1. No Visual Studio, crie um aplicativo em JavaScript que use o modelo de projeto do Aplicativo Dinâmico do Windows Phone.

2. Com o modelo aberto no Visual Studio, selecione **emulador 8,1 WVGA 4IN 512MB** na lista suspensa na barra de ferramentas de depuração no depurador:

     ![Selecionando um destino de depuração](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Pressione F5 para executar o aplicativo no modo de depuração.

4. No aplicativo em execução, vá para a **seção 3** item dinâmico.

5. Alterne para o Visual Studio (Alt+Tab ou F12).

6. No Explorador do DOM, escolha `Find` no canto superior direito.

7. Digite `ListView`e pressione Enter.

8. Se necessário, escolha o botão **Avançar** para localizar o `DIV` elemento que representa o `ListView` controle (esse elemento tem um `data-win-control` valor de `WinJS.UI.ListView` ).

     Agora o elemento `DIV` deve ser selecionado no Explorador do DOM.

9. Escolha a guia **eventos** no painel no lado direito do explorador do dom.

     Agora você pode ver os eventos que têm assinantes ativos para o elemento `DIV`, conforme mostrado aqui.

     ![Guia eventos do explorador do DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Para localizar os ouvintes desses eventos, escolha os links dos arquivos JavaScript associados.

11. Para identificar rapidamente os ouvintes de eventos para elementos pai na hierarquia de DOM, escolha o elemento pai na lista de hierarquias na parte inferior do Explorador do DOM.

     ![Selecionando elementos pai na hierarquia DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     A guia **eventos** mostra ouvintes de eventos para qualquer elemento que você escolher na lista hierarquia.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Dicas para resolver problemas com ouvintes de eventos
 Em alguns cenários de aplicativo, os ouvintes de evento devem ser removidos explicitamente usando [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Use a guia **eventos** no explorador do dom para testar se os ouvintes de eventos foram removidos dos elementos DOM durante a execução do código. Aqui estão algumas dicas para ajudar a resolver esses tipos de problemas:

- Para aplicativos que usam o modelo de navegação de página única implementado nos modelos de [projeto](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)do Visual Studio, normalmente não é necessário remover ouvintes de eventos registrados para objetos, como elementos DOM, que fazem parte de uma página. Neste cenário, um elemento DOM e seus ouvintes de evento associados têm a mesma duração e podem ser coletados como lixo.

- Se a duração do elemento DOM ou objeto for diferente do ouvinte de evento associado, pode ser necessário chamar o método `removeEventListener`. Por exemplo, se você usar o evento `window.onresize`, pode ser necessário remover o ouvinte de evento se você navegar para fora da página em que manipula o evento.

- Se o `removeEventListener` falhar ao remover o ouvinte especificado, ele pode estar sendo chamado em uma instância do objeto diferente. Você pode usar o método de [método de associação (função)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) para resolver esse problema ao adicionar o ouvinte.

- Para remover um ouvinte de eventos que foi adicionado usando o [método de associação (função)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) ou usando uma função anônima, armazene uma instância da função ao adicionar o ouvinte. Aqui está uma maneira de usar este padrão com segurança:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Se você usar o código a seguir em vez de armazenar uma referência à função associada, você não conseguirá remover explicitamente o ouvinte de evento:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- Você não pode remover um ouvinte de evento usando `removeEventListener` se ele foi adicionado com o atributo `obj.on<eventname>`, por exemplo, `window.onresize = handlerFunc`.

- Use o analisador de memória JavaScript para a [memória JavaScript](../profiling/javascript-memory.md) em seu aplicativo. Os ouvintes de evento que devem ser explicitamente removidos podem aparecer como perda de memória.

## <a name="see-also"></a>Consulte Também

- [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
- [Depurar estilos CSS com o Explorador do DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Depurar o layout com o Explorador do DOM](../debugger/debug-layout-using-dom-explorer.md)