---
title: Lista de eventos de gráficos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b1d8bdeb4497af57c385e73ff0dcd34041a2097
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297327"
---
# <a name="graphics-event-list"></a>Lista de eventos do gráfico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use a lista de eventos gráficos no Analisador de Gráficos do Visual Studio para explorar os eventos do Direct3D que foram registrados durante a renderização de um quadro de seu jogo ou aplicativo.  
  
 Esta é a lista de eventos:  
  
 ![Uma lista de eventos que têm "index" em seu nome.](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Usando a lista de eventos  
 Quando você seleciona um evento na lista de eventos, ele é refletido nas informações exibidas por outras ferramentas de análise de gráficos; usando a lista de eventos em conjunto com essas outras ferramentas, você pode examinar um problema de renderização em detalhes para determinar sua causa. Para saber mais sobre como você pode resolver problemas de renderização usando a lista de eventos junto com outras ferramentas de análise de gráficos, consulte [exemplos](../debugger/graphics-diagnostics-examples.md).  
  
 O uso dos recursos da lista de eventos de maneira efetiva é importante para contornar quadros complexos que podem conter milhares de eventos. Para usar a lista de eventos de maneira efetiva, escolha a exibição que funcione melhor para você, use a pesquisa para filtrar a lista de eventos, siga os links para saber mais sobre os objetos Direct3D associados a um evento e use os botões de seta para alternar rapidamente chamadas de desenho.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Eventos codificados por cores no Direct3D 12  
 O Direct3D 12 expõe várias filas que correspondem a uma funcionalidade de hardware diferente. Para ajudar a identificar a fila associada a um evento de gráficos específico no Direct3D 12, os eventos são codificados por cores na lista de eventos de acordo com sua fila quando você está trabalhando com uma captura de um aplicativo do Direct3D 12.  
  
|Fila do Direct3D 12|Cor|  
|-----------------------|-----------|  
|Processar fila|Verde|  
|Fila de computação|Amarelo|  
|Copiar fila|Laranja|  
  
 O Direct3D 11 não expõe várias filas, portanto, os eventos não são codificados por cores na lista de eventos quando você está trabalhando com uma captura de um aplicativo do Direct3D 11.  
  
### <a name="event-list-views"></a>Exibições da lista de eventos  
 A lista de eventos oferece suporte a duas exibições diferentes que organizam eventos de gráficos de maneiras distintas para dar suporte ao fluxo de trabalho e às preferências. A primeira exibição é o *modo de exibição de chamadas de desenho*, que organiza eventos e seu estado associado de maneira hierárquica. A segunda exibição é o *modo de exibição da linha do tempo*, que organiza eventos cronologicamente, em uma lista plana.  
  
 A exibição **Chamadas de Desenho**  
 Exibe eventos capturados e seu estado em uma hierarquia. O nível superior da hierarquia é constituído de eventos como chamadas de desenho, limpezas, presentes e os que lidam com exibições. Na lista de eventos, é possível expandir chamadas de desenho para exibir o estado atual do dispositivo no momento da chamada de desenho. E você ainda pode expandir cada tipo de estado para exibir os eventos que definem seus valores. Nesse nível, também é possível ver se um determinado estado foi definido em um quadro anterior ou se ele foi definido mais de uma vez desde a chamada de desenho mais recente.  
  
 O modo de exibição de **Linha do tempo**  
 Exibe cada evento capturado em ordem cronológica. Essa forma de organizar a lista de eventos é a mesma de versões anteriores do Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Para alterar o modo de exibição da lista de eventos  
  
- Na janela **Lista de Eventos de Gráficos**, acima da lista de eventos, localize o menu suspenso **Exibir** e escolha a exibição **Linha do Tempo** ou **Chamadas de Desenho**.  
  
### <a name="filtering-events"></a>Filtrando eventos  
 É possível usar a caixa Pesquisar, localizada no canto superior direito da janela **Lista de Eventos de Gráficos**, para filtrar a lista de eventos e incluir apenas eventos cujos nomes contenham palavras-chave específicas. Você pode especificar palavras-chave únicas, como `Vertex`, conforme mostrado na ilustração anterior — ou várias palavras-chave usando uma lista delimitada por ponto-e-vírgula, como `Draw;Primitive`— que corresponde a eventos que têm `Draw` ou `Primitive` em seus nomes. As pesquisas são sensíveis ao espaço em branco — por exemplo, `VSSet` e `VS Set` são pesquisas diferentes — portanto, certifique-se de formar pesquisas com cuidado.  
  
### <a name="moving-between-draw-calls"></a>Alternando entre chamadas de desenho  
 Como o exame de chamadas `Draw` é especialmente importante, é possível usar os botões **Ir para a próxima chamada de desenho** e **Ir para a chamada de desenho anterior**, localizados no canto superior esquerdo da janela **Lista de Eventos de Gráficos**, para encontrar e alternar rapidamente entre chamadas de desenho.  
  
### <a name="links-to-graphics-objects"></a>Links a objetos de gráficos  
 Para entender determinados eventos gráficos, talvez seja necessário obter informações adicionais sobre o estado atual do Direct3D ou sobre objetos Direct3D que são referenciados pelo evento. Muitos eventos fornecem links a essas informações, que é possível seguir para obter mais detalhes.  
  
## <a name="kinds-of-events-and-event-markers"></a>Tipos de eventos e marcadores de eventos  
 Os eventos exibidos na lista de eventos são organizados em quatro categorias: eventos gerais, eventos de desenho, grupos de eventos definidos pelo usuário e marcadores de evento definidos pelo usuário. Exceto no caso de eventos em geral, cada evento é exibido com um ícone que indica a categoria a que pertence.  
  
|Ícone|Descrição do evento|  
|----------|-----------------------|  
|(sem ícone)|Evento em geral<br /> Qualquer evento que não seja um evento definido pelo usuário, um grupo de eventos definido pelo usuário ou um evento de desenho.|  
|![O ícone de evento de desenho](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Evento de desenho<br /> Marca um evento de desenho ocorrido durante o quadro capturado.|  
|![O ícone&#45;de marcador de evento definido pelo usuário](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Grupo de eventos definido pelo usuário<br /> Eventos relacionados a grupos, conforme definido pelo aplicativo.|  
|![O ícone&#45;de marcador de evento definido pelo usuário](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Marcador de evento definido pelo usuário<br /> Marca um local específico, conforme definido pelo aplicativo.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Marcando eventos definidos pelo usuário em seu aplicativo  
 Os eventos definidos pelo usuário são específicos do aplicativo. É possível usá-los para correlacionar eventos significativos ocorridos no aplicativo com eventos na Lista de Eventos de Gráficos. Por exemplo, é possível criar grupos de eventos definidos pelo usuário para organizar eventos relacionados, como os que renderizam a interface do usuário, em grupos ou em hierarquias de forma que você possa navegar na lista de eventos mais facilmente ou criar marcadores quando determinados tipos de objetos forem utilizados para encontrar de maneira fácil os eventos de gráficos na lista de eventos.  
  
 Para criar grupos e marcadores no aplicativo, você usa as mesmas APIs fornecidas pelo Direct3D a serem usadas por outras ferramentas de depuração do Direct3D. Essas APIs às vezes mudam entre as versões do Direct3D, mas a funcionalidade básica é a mesma.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Eventos definidos pelo usuário no Direct3D 12  
 Para criar grupos e marcadores no Direct3D 12, use as APIs descritas nesta seção. A tabela a seguir resume as APIs que você pode usar dependendo se você estiver marcando eventos em uma fila de comando ou em uma lista de comandos.  
  
|Descrição da API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Verificar disponibilidade de evento definida pelo usuário|[PIXGetStatus](https://msdn.microsoft.com/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](https://msdn.microsoft.com/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Iniciar um grupo de eventos|[PIXBeginEvent](https://msdn.microsoft.com/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](https://msdn.microsoft.com/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Terminar um grupo de eventos|[PIXEndEvent](https://msdn.microsoft.com/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](https://msdn.microsoft.com/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Criar um marcador de evento|[PIXSetMarker](https://msdn.microsoft.com/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](https://msdn.microsoft.com/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Eventos definidos pelo usuário no Direct3D 11 e anteriores  
 Para criar grupos e marcadores no Direct3D 11 ou anterior, use as APIs descritas nesta seção. A tabela a seguir resume as APIs que você pode usar para versões diferentes do Direct3D 11 e versões anteriores do Direct3D.  
  
|Descrição da API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](https://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11,1)|Família de API D3DPerf_ (Direct3D 11,0 e anterior)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Iniciar um grupo de eventos|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Terminar um grupo de eventos|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Criar um marcador de evento|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 É possível usar qualquer uma dessas APIs compatíveis com a versão do Direct3D. Por exemplo, se estiver segmentando a API Direct3D 11.1, você poderá usar `SetMarker` ou `D3DPerf_SetMarker` para criar um marcador de evento, mas não `SetMarkerInt`, porque ele só está disponível no Direct3D 11.2, e não é possível misturar aqueles compatíveis com versões diferentes do Direct3D no mesmo aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: objetos ausentes devido ao estado do dispositivo](../debugger/walkthrough-missing-objects-due-to-device-state.md)
