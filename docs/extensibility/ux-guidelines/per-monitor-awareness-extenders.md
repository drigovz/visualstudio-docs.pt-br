---
title: Suporte a reconhecimento por Monitor Extensores do Visual Studio
titleSuffix: ''
description: Saiba mais sobre o novo suporte de extensor para por monitor-reconhecimento disponível no Visual Studio de 2019.
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477673"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Suporte a reconhecimento por Monitor Extensores do Visual Studio

Versões anteriores do Visual Studio de 2019 tinham seu contexto de reconhecimento DPI definido como ciente do sistema, em vez de um monitor DPI ciente (PMA). Em execução no sistema de reconhecimento resultou em uma experiência visual inadequada (por exemplo, desfocadas fontes ou ícones) sempre que o Visual Studio tinha que renderizar em vários monitores com fatores de escala diferente ou remoto em computadores com configurações de exibição diferente (por exemplo, diferentes Windows dimensionamento).

O contexto de reconhecimento DPI de 2019 do Visual Studio é o conjunto como ciente, permitindo que o Visual Studio para renderizar de acordo com a configuração da exibição onde ele esteja hospedado por monitor em vez de uma configuração genérica do sistema definida. Traduzindo, por fim, para uma interface do usuário nítida para áreas de superfície que implementam o suporte PMA.

Consulte a [desenvolvimento de aplicativos de área de trabalho DPI alto no Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) documentação para obter mais informações sobre os termos e o cenário geral abordados neste documento.

## <a name="quickstart"></a>Guia de Início Rápido
- Verifique se o Visual Studio está em execução no modo PMA (consulte **PMA habilitando**)

- Validar sua extensão funciona corretamente em um conjunto de cenários comuns (consulte **teste suas extensões para problemas PMA**)

- Se você encontrar problemas, você precisará adicionar o novo pacote de preciosidade PMA, diagnosticar e corrigir problemas usando as estratégias e recomendações discutidas neste documento

## <a name="enabling-pma"></a>Habilitando PMA
Para habilitar PMA no Visual Studio, os requisitos a seguir precisam ser atendidos:
1)  10 de abril de 2018 do Windows Update (v1803 RS4) ou posterior
2)  .NET framework 4.8 RTM ou superior (no momento é fornecido como visualização autônoma ou o pacote com a recente Windows builds do Insider)
3)  Visual Studio de 2019 com o ["Otimizar o processamento para telas com densidades de pixels diferente"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) opção habilitada

Quando esses requisitos forem atendidos, o Visual Studio habilitará automaticamente PMA entre o processo.

## <a name="testing-your-extensions-for-pma-issues"></a>Teste suas extensões para problemas PMA

Visual Studio oficialmente dá suporte a estruturas de WPF, Windows Forms, Win32 e da interface do usuário de HTML/JS. Quando o Visual Studio será colocado no modo PMA, as pilhas de interface do usuário diferentes se comportam diferentemente. Portanto, independentemente da estrutura de interface do usuário, é recomendável que uma aprovação de teste é executada para garantir que toda interface do usuário está em conformidade com PMA.

Independentemente da estrutura de interface do usuário oferece suporte a sua extensão, é recomendável que você valide os seguintes cenários comuns:

1. Alterando o fator de escala de um ambiente de monitor único, enquanto o aplicativo está em execução *
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à alteração de DPI do Windows dinâmica

2. Encaixe/desencaixar um laptop em que um monitor conectado é definido como primário e o monitor conectado tem um fator de escala diferente que o primário enquanto o aplicativo está em execução.
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à exibição, alteração de DPI, bem como manipulação exibe dinamicamente sendo adicionado ou removido

3. Ter vários monitores com fatores de escala diferente e mover o aplicativo, entre eles.
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à alteração DPI de exibição
    
4. Comunicação remota em um computador quando as máquinas locais e remotas têm fatores de escala diferente para o monitor principal.
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à alteração de DPI do Windows dinâmica

Um bom teste preliminar para se a interface do usuário pode ter problemas é ou não o código utiliza o *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* ou *Microsoft.VisualStudio.PlatformUI.DpiHelper* classes. Essas classes DpiHelper antigos só há suporte para reconhecimento de DPI do sistema e sempre não funcionarão corretamente quando o processo for PMA.

Um uso típico desses DpiHelpers se parecerá com:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

No exemplo anterior, um retângulo que representa os limites lógicos de uma janela é convertido em unidades de dispositivo para que ele pode ser passado para o método nativo MonitorFromPoint que espera as coordenadas do dispositivo para retornar um ponteiro de monitor precisos de volta.

### <a name="classes-of-issues"></a>Classes de problemas

Quando PMA está habilitado para o Visual Studio, a interface do usuário foi possível replicar os problemas de várias maneiras comuns. A maioria, se não todos, esses problemas podem ocorrer em qualquer uma das estruturas de interface do usuário com suporte do Visual Studio. Além disso, esses problemas podem ocorrer até mesmo quando uma parte da interface do usuário está sendo hospedada em cenários de dimensionamento de DPI de modo misto (consulte o Windows [documentação](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) para saber mais). 

#### <a name="win32-window-creation"></a>Criação da janela Win32
Ao criar o windows com CreateWindow() ou CreateWindowEx(), um padrão comum é criar a janela nas coordenadas 0,0 (o canto superior/esquerdo da tela principal), em seguida, movê-lo para sua posição final. No entanto, fazer isso pode fazer com que a janela disparar um DPI alterado mensagem ou evento, que pode disparar novamente outras mensagens de interface do usuário ou os eventos e eventualmente levar ao comportamento indesejado ou renderização.

#### <a name="wpf-element-placement"></a>Posicionamento de elemento do WPF
Ao mover elementos do WPF usando o antigo Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, as coordenadas do canto superior esquerdo podem não ser calculadas corretamente sempre que elementos são o caso de DPI não primário.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialização de tamanhos de elemento de interface do usuário ou posições
Sempre que o tamanho da interface do usuário ou a posição for restaurada em um contexto DPI diferente que o que ele foi armazenado no, ele será posicionado e dimensionado incorretamente. Isso acontece porque os limites lógicos de uma janela são convertidos em unidades de dispositivo para que ele pode ser passado para o método Win32 MonitorFromPoint que espera as coordenadas do dispositivo para retornar um ponteiro de monitor precisos de volta.

#### <a name="incorrect-scaling"></a>Dimensionamento incorreto
Elementos de interface do usuário criados na DPI primário serão dimensionado corretamente, no entanto, quando movido para uma exibição com um valor de DPIS diferente, eles não redimensione e assim, o seu conteúdo acaba sendo muito grande ou muito pequeno.

#### <a name="incorrect-bounding"></a>Delimitação incorreto
Da mesma forma, para o problema de colocação em escala, elementos de interface do usuário irá calcular seus limites corretamente em seu contexto DPI primário, no entanto, quando movido para um DPI não primário, eles não calculam corretamente os novos limites. Como tal, a janela de conteúdo acaba sendo muito grande ou muito pequeno em comparação com a hospedagem da interface do usuário, que resulta em espaço vazio ou recorte.

#### <a name="drag--drop"></a>Arrastar e soltar
Sempre que dentro de cenários DPI de modo misto (por exemplo, diferentes elementos interface do usuário no contexto DPI primário e secundários de renderização), arrastar e soltar coordenadas poderiam ser erro de cálculo, resultando na posição final soltar acaba incorreto.

#### <a name="out-of-process-ui"></a>Interface do usuário de fora do processo
Algumas interfaces do usuário é criado fora do processo e se o processo de criação externo estiver em um modo de reconhecimento DPI diferente que o Visual Studio, isso pode introduzir problemas de renderização anterior.

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Controles dos Windows Forms, imagens ou windows não exibidos
Uma das principais causas para esse problema é que os desenvolvedores que tentarem reassociar um controle ou janela com um DpiAwarenessContext para uma janela diferente do DpiAwarenessContext. 

As imagens a seguir mostram as restrições do sistema operacional Windows atuais no windows, gerenciamento do domínio pai, a menos que o comportamento de hospedagem de thread seja explicitamente alterado:

![Uma captura de tela do comportamento correto paternidade](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

Como resultado, se você definir a relação pai-filho entre os modos sem suporte, ele falhará e o controle ou janela não pode ser renderizada conforme o esperado.

### <a name="diagnosing-issues"></a>Diagnosticando problemas
Há muitos fatores a considerar ao identificar problemas relacionados à PMA: 

1. Faz a interface do usuário ou a API esperado lógico ou valores de dispositivo.
    - WPF UI e APIs normalmente usa valores lógicos (mas nem sempre)
    - Interface do usuário do Win32 e APIs normalmente usa valores de dispositivo

2. Em que os valores são provenientes?
    - Se receber valores de outra interface do usuário ou a API, é o dispositivo de passagem ou valores lógicos.
    - Se receber valores de várias fontes, todas as use/esperam que os mesmos tipos de valores ou conversões precisa ser misturadas e combinadas?

3. São constantes de interface do usuário em uso e de que forma eles estão?

4. É o thread no contexto correto de DPI para os valores está recebendo?
    - As alterações para habilitar CLMM geralmente devem colocar os caminhos de código no contexto certo, no entanto, o trabalho feito fora do fluxo de evento ou loop de mensagem principal pode executar no contexto errado de DPI.

5. O valores cruzar os limites de contexto do DPI?
    - Arrastar e soltar é uma situação comum em que as coordenadas podem cruzar os contextos DPI. Janela tenta fazer a coisa certa, mas em alguns casos, o host da interface do usuário talvez precise fazer o trabalho de conversão para garantir que os limites de contexto correspondente.

### <a name="pma-nugget-package"></a>Pacote NuGet PMA
As novas bibliotecas DpiAwarness podem ser encontradas no pacote Microsoft.VisualStudio.DpiAwareness NuGet.

### <a name="recommended-tools"></a>Ferramentas recomendadas
As seguintes ferramentas podem ajudar a depurar problemas relacionados à PMA entre algumas das diferentes pilhas de interface do usuário com suporte do Visual Studio.

#### <a name="snoop"></a>Rastrear
Snoop é uma ferramenta de depuração de XAML que tem algumas funcionalidades adicionais que as ferramentas internas de XAML do Visual Studio não tem. Além disso, Snoop não precisa depurar ativamente o Visual Studio para ser capaz de exibir e ajustar sua UI WPF. As duas maneiras principais Snoop pode ser útil para diagnosticar problemas PMA é para validar as coordenadas de posicionamento lógico ou limites de tamanho, e para validar a interface do usuário tem o direito DPI.
 
#### <a name="visual-studio-xaml-tools"></a>Ferramentas do Visual Studio XAML
Como Snoop, as ferramentas XAML no Visual Studio podem ajudar a diagnosticar problemas PMA. Depois que um provável culpado for encontrado, você pode definir pontos de interrupção e usar a janela Live Visual Tree, bem como as janelas de depuração, para inspecionar os limites da interface do usuário e DPI atual.

## <a name="strategies-for-fixing-pma-issues"></a>Estratégias para corrigir problemas PMA

### <a name="replacing-dpihelper-calls"></a>A substituição das chamadas de DpiHelper
Na maioria dos casos, corrigindo problemas de interface do usuário em PMA se resume a substituição das chamadas em código gerenciado e o antigo: *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* e *Microsoft.VisualStudio.PlatformUI.DpiHelper* classes com chamadas para o novo *Microsoft.VisualStudio.Utilities.DpiAwareness* classe auxiliar. 

Para código nativo, ele envolvem substituindo chamadas para o antigo *VsUI::CDpiHelper* classe com chamadas para o novo *VsUI::CDpiAwareness* classe. As novas classes DpiAwareness e CDpiAwareness oferecem os mesmos auxiliares de conversão como as classes DpiHelper, mas não requerem um parâmetro de entrada adicional: o elemento de interface do usuário a ser usado como uma referência para a operação de conversão. 

A classe DpiAwareness gerenciada oferece auxiliares para elementos visuais do WPF, controles de formulários do Windows e Win32 HWNDs e HMONITORs (ambos na forma de IntPtrs), enquanto os nativo CDpiAwareness ofertas HWND e HMONITOR auxiliares da classe.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Caixas de diálogo do Windows Forms, windows ou controles exibidos no DpiAwarenessContext errado
Mesmo após uma paternidade bem-sucedida do windows com DpiAwarenessContext diferente (devido ao comportamento de padrão do windows), usuários ainda poderão ver problemas de dimensionamento, como janelas de DpiAwarenessContext diferentes dimensionamento diferente. Como resultado, usuários poderão ver os problemas de imagem ou texto desfocado/de alinhamento da interface do usuário.

A solução é definir o escopo de DpiAwarenessContext correto para todas as janelas e controles no aplicativo.

### <a name="tlmm-dialogs"></a>Caixas de diálogo TLMM
Ao criar janelas de nível superior, como caixas de diálogo modais, é importante garantir que o thread está no estado correto antes do HWND que está sendo criado. O thread pode ser colocado no reconhecimento de sistema, usando o auxiliar de CDpiScope no formato nativo ou gerenciado o auxiliar DpiAwareness.EnterDpiScope no. (TLMM geralmente deve ser usada em caixas de diálogo de não-WPF/windows.)

### <a name="child-level-mixed-mode-clmm"></a>Nível filho de modo misto (CLMM)

Por padrão, janelas filho recebem o mesmo modo de reconhecimento de DPI seus pais. No entanto, você pode usar SetThreadDpiHostingBehavior substituí-la e executaram janelas filho em um modo de dimensionamento diferente que seu pai ou host.


#### <a name="clmm-issues"></a>Problemas CLMM
Grande parte do trabalho de cálculo de interface do usuário ocorre como parte da principal mensagens loop ou evento cadeia já deve estar executando no contexto certo de DPI. No entanto, se coordenada ou cálculos de dimensionamento são feitos fora desses fluxos de trabalho principais (como durante uma tarefa de tempo ocioso, ou fora do thread de interface do usuário, o contexto atual de DPI pode estar incorreto levando a localização errada da interface do usuário ou problemas de dimensionamento incorretamente. Colocando o thread no estado correto para a interface do usuário trabalho geralmente corrige o problema.
 
#### <a name="opting-out-of-clmm"></a>Recusa da CLMM
Se uma janela de ferramentas não-WPF estiver sendo migrada para dar total suporte PMA, precisará recusar CLMM. Para fazer isso, uma nova interface precisa ser implementado: IVsDpiAware.

C#:
```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++:
```cplusplus
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```
 

Para linguagens gerenciadas, o melhor lugar para implementar esta interface está na mesma classe que deriva de *Microsoft.VisualStudio.Shell.ToolWindowPane*. Para C++, o melhor lugar para implementar esta interface está na mesma classe que implementa *ivswindowpane e* de vsshell.h.

O valor retornado pela propriedade de modo na interface é um __VSDPIMODE (e conversão para uint no managed):

```cs
enum __VSDPIMODE
    {
        VSDM_Unaware    = 0x01,
        VSDM_System     = 0x02,
        VSDM_PerMonitor = 0x03,
    }
```

- Significa que não reconhecem que a janela da ferramenta precisa lidar com 96 DPI, Windows manipulará a dimensioná-lo para todos os outros DPIs. Resultando no conteúdo que está sendo um pouco desfocado.
- A janela da ferramenta precisa lidar com o DPI para o primário de meios de sistema exibem DPI. Qualquer exibição com uma correspondência DPI parecerá nítida, mas se o DPI diferente ou altera durante a sessão, Windows manipulará a colocação em escala e será um pouco desfocado.
- PerMonitor significa que a janela da ferramenta precisa lidar com todos os DPIs em todos os vídeos e sempre que o DPI é alterado.

**OBSERVAÇÃO**: Visual Studio suporta apenas PerMonitorV2 reconhecimento, portanto, o valor de enumeração PerMonitor convertida para o valor de Windows do DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

## <a name="known-issues"></a>Problemas conhecidos

### <a name="windows-forms"></a>Windows Forms

Para otimizar os novos cenários de modo misto, o Windows Forms alterado como ele cria controles e janelas sempre que seu pai não foi explicitamente definido. Anteriormente, controles sem um pai explícito usado um "estacionamento janela interno" como um pai temporário para o controle ou janela que está sendo criada. 

A "janela de estacionamento" obtém seu DpiAwarenessContext do processo que o aplicativo é executado sob. O controle herda o mesmo DpiAwarenessContext como a janela de estacionamento e, em seguida, poderia ser reassociado ao pai original/esperada pelo desenvolvedor do aplicativo.  Isso não funciona quando o pai pretendido para o controle não é o mesmo DpiAwarenessContext como o controle que está sendo criado.

A partir do .NET 4.8, se o pai não for definido explicitamente no controle ou janela, Windows Forms será de consulta para uma janela de estacionamento que corresponda a DpiAwarenessContext do thread no qual a criação de controle ou janela é solicitada e usá-lo como um pai temporário. Em outras palavras, no momento da criação de controle agora é criado com o DpiAwarenessContext pretendido. O controle ou janela, em seguida, será ser reassociada ao pai esperado pelo desenvolvedor do aplicativo.
