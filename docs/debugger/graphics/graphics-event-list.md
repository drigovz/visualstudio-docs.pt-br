---
title: Lista de eventos gráficos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5c4e8f39ff77779985536e53d98ddc2785b109b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302122"
---
# <a name="graphics-event-list"></a>Lista de eventos do gráfico
Use a Lista de Eventos Gráficos no Visual Studio Graphics Analyzer para explorar os eventos Direct3D que foram gravados durante a renderização de um quadro do seu jogo ou aplicativo.

 Esta é a Lista de Eventos:

 ![Uma lista de eventos que têm "Índice" em seu nome.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Usando a lista de eventos
 Quando você seleciona um evento na lista de eventos, ele é refletido nas informações exibidas por outras ferramentas de Análise Gráfica; usando a lista de eventos em conjunto com essas outras ferramentas, você pode examinar um problema de renderização em detalhes para determinar sua causa. Para saber mais sobre como resolver problemas de renderização usando a lista de eventos juntamente com [outras](graphics-diagnostics-examples.md)ferramentas de Análise Gráfica, consulte Exemplos .

 O uso dos recursos da lista de eventos de maneira efetiva é importante para contornar quadros complexos que podem conter milhares de eventos. Para usar a lista de eventos de maneira efetiva, escolha a exibição que funcione melhor para você, use a pesquisa para filtrar a lista de eventos, siga os links para saber mais sobre os objetos Direct3D associados a um evento e use os botões de seta para alternar rapidamente chamadas de desenho.

### <a name="color-coded-events-in-direct3d-12"></a>Eventos codificados por cores no Direct3D 12
 O Direct3D 12 expõe várias filas que correspondem a diferentes funcionalidades de hardware. Para ajudar a identificar a fila associada a um evento gráfico específico no Direct3D 12, os eventos são codificados por cores na Lista de Eventos de acordo com sua fila quando você está trabalhando com uma captura de um aplicativo Direct3D 12.

|Fila do Direct3D 12|Color|
|-----------------------|-----------|
|Fila de renderização|Verde|
|Fila de cálculo|Amarelo|
|Fila de cópias|Laranja|

 O Direct3D 11 não expõe várias filas, portanto, os eventos não são codificados por cores na Lista de Eventos quando você está trabalhando com uma captura de um aplicativo Direct3D 11.

### <a name="event-list-views"></a>Exibições da lista de eventos
 A lista de eventos oferece suporte a duas exibições diferentes que organizam eventos de gráficos de maneiras distintas para dar suporte ao fluxo de trabalho e às preferências. A primeira visualização é a visão de trabalho da *GPU* que organiza eventos e seu estado associado hierarquicamente. A segunda exibição é o *modo de exibição da linha do tempo*, que organiza eventos cronologicamente, em uma lista plana.

 A **exibição GPU Work** exibe eventos capturados e seu estado em uma hierarquia. O nível superior da hierarquia é constituído de eventos como chamadas de desenho, limpezas, presentes e os que lidam com exibições. Na lista de eventos, é possível expandir chamadas de desenho para exibir o estado atual do dispositivo no momento da chamada de desenho. E você ainda pode expandir cada tipo de estado para exibir os eventos que definem seus valores. Nesse nível, também é possível ver se um determinado estado foi definido em um quadro anterior ou se ele foi definido mais de uma vez desde a chamada de desenho mais recente.

 A **exibição Linha do Tempo** exibe cada evento capturado em ordem cronológica. Essa forma de organizar a lista de eventos é a mesma de versões anteriores do Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Para alterar o modo de exibição da lista de eventos

- Na janela **Lista de eventos gráficos,** acima da lista de eventos, localize a **exibição** em isaque e escolha a exibição **Linha do Tempo** ou a exibição **GPU Work.**

### <a name="filtering-events"></a>Filtragem de eventos
 É possível usar a caixa Pesquisar, localizada no canto superior direito da janela **Lista de Eventos de Gráficos**, para filtrar a lista de eventos e incluir apenas eventos cujos nomes contenham palavras-chave específicas. Você pode especificar `Vertex`palavras-chave únicas como — como mostrado na ilustração anterior `Draw;Primitive`— ou várias `Draw` palavras-chave usando uma lista delimitada de ponto e vírgula — que corresponde a eventos que têm ou `Primitive` em seus nomes. As pesquisas são sensíveis ao `VSSet` espaço `VS Set` em branco , por exemplo, e são pesquisas diferentes, por isso, certifique-se de formar pesquisas cuidadosamente.

### <a name="moving-between-draw-calls"></a>Alternando entre chamadas de desenho
 Como o exame de chamadas `Draw` é especialmente importante, é possível usar os botões **Ir para a próxima chamada de desenho** e **Ir para a chamada de desenho anterior**, localizados no canto superior esquerdo da janela **Lista de Eventos de Gráficos**, para encontrar e alternar rapidamente entre chamadas de desenho.

### <a name="links-to-graphics-objects"></a>Links a objetos de gráficos
 Para entender certos eventos gráficos, você pode precisar de informações adicionais sobre o estado atual do Direct3D ou sobre objetos Direct3D que são referenciados pelo evento. Muitos eventos fornecem links a essas informações, que é possível seguir para obter mais detalhes.

## <a name="kinds-of-events-and-event-markers"></a>Tipos de eventos e marcadores de eventos
 Os eventos exibidos na lista de eventos são organizados em quatro categorias: eventos gerais, eventos de desenho, grupos de eventos definidos pelo usuário e marcadores de evento definidos pelo usuário. Exceto no caso de eventos em geral, cada evento é exibido com um ícone que indica a categoria a que pertence.

|ícone|Descrição do evento|
|----------|-----------------------|
|(sem ícone)|Evento em geral<br /> Qualquer evento que não seja um evento definido pelo usuário, um grupo de eventos definido pelo usuário ou um evento de desenho.|
|![O ícone do evento de sorteio](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Evento de desenho<br /> Marca um evento de desenho ocorrido durante o quadro capturado.|
|![O ícone de marcador de evento&#45;definido pelo usuário](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Grupo de eventos definido pelo usuário<br /> Eventos relacionados a grupos, conforme definido pelo aplicativo.|
|![O ícone de marcador de evento&#45;definido pelo usuário](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Marcador de evento definido pelo usuário<br /> Marca um local específico, conforme definido pelo aplicativo.|

## <a name="marking-user-defined-events-in-your-app"></a>Marcando eventos definidos pelo usuário em seu aplicativo
 Os eventos definidos pelo usuário são específicos do aplicativo. É possível usá-los para correlacionar eventos significativos ocorridos no aplicativo com eventos na Lista de Eventos de Gráficos. Por exemplo, é possível criar grupos de eventos definidos pelo usuário para organizar eventos relacionados, como os que renderizam a interface do usuário, em grupos ou em hierarquias de forma que você possa navegar na lista de eventos mais facilmente ou criar marcadores quando determinados tipos de objetos forem utilizados para encontrar de maneira fácil os eventos de gráficos na lista de eventos.

 Para criar grupos e marcadores no aplicativo, você usa as mesmas APIs fornecidas pelo Direct3D a serem usadas por outras ferramentas de depuração do Direct3D. Essas APIs às vezes mudam entre versões do Direct3D, mas a funcionalidade básica é a mesma.

### <a name="user-defined-events-in-direct3d-12"></a>Eventos definidos pelo usuário no Direct3D 12
 Para criar grupos e marcadores no Direct3D 12, use as APIs descritas nesta seção. A tabela abaixo resume as APIs que você pode usar dependendo se você está marcando eventos em uma fila de comando ou lista de comandos.

|Descrição da API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Verifique a disponibilidade do evento definido pelo usuário|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Iniciar um grupo de eventos|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Terminar um grupo de eventos|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Criar um marcador de evento|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Eventos definidos pelo usuário no Direct3D 11 e anteriores
 Para criar grupos e marcadores no Direct3D 11 ou anterior, use as APIs descritas nesta seção. A tabela abaixo resume as APIs que você pode usar para diferentes versões do Direct3D 11 e versões anteriores do Direct3D.

|Descrição da API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefininotnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ família API (Direct3D 11.0 e anterior)|
|---------------------| - | - | - |
|Iniciar um grupo de eventos|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Terminar um grupo de eventos|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Criar um marcador de evento|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 É possível usar qualquer uma dessas APIs compatíveis com a versão do Direct3D. Por exemplo, se estiver segmentando a API Direct3D 11.1, você poderá usar `SetMarker` ou `D3DPerf_SetMarker` para criar um marcador de evento, mas não `SetMarkerInt`, porque ele só está disponível no Direct3D 11.2, e não é possível misturar aqueles compatíveis com versões diferentes do Direct3D no mesmo aplicativo.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Histórico de recursos
Visual Studio 2017 e maior estoam a janela **Histórico de Recursos.**  Selecionar o ícone ![](media/gfx_watch.png) do relógio ao lado de uma entrada na janela **Lista de eventos** trará a janela Histórico de **recursos** mostrado abaixo:

![Histórico de recursos](media/gfx_diag_resource_history.png)

Esta janela permite que você visualize o histórico do item selecionado na lista de eventos.  O dropdown na parte superior pode ser usado para selecionar outros itens para visualizar o histórico de.  A metade superior da janela contém os **Eventos de configuração de quadros**.  Estes são os eventos que se enquadram na categoria *Criar* tipo e são chamadas que normalmente inicializam e criam o recurso.  A metade inferior da janela contém a seção **Eventos do Quadro.**  Estes são os eventos normais de leitura e gravação que ocorrem durante o uso do recurso.

| Coluna | Descrição |
|-----------| - |
| **Tipo** | Mostra o tipo de entrada, normalmente *Criar,* *Ler* e *Escrever*. |
| **Exibir** | Mostra uma miniatura do recurso naquele momento no tempo.  Clique duas vezes na miniatura para abrir uma exibição de detalhes do recurso naquele momento. |
| **Evento** | Mostra a chamada de método que ocorreu que gerou o evento.  Qualquer histórico adicional em itens individuais pode ser visualizado](media/gfx_watch.png) selecionando o ícone do ![relógio na linha apropriada.  Além disso, qualquer item que for `m_commandList` desenhado em texto azul, como na captura de tela acima, pode ser selecionado para mais detalhes. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Confira também
- [Instruções passo a passo: objetos ausentes devido ao estado do dispositivo](walkthrough-missing-objects-due-to-device-state.md)