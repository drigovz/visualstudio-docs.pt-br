---
title: Suporte a reconhecimento por Monitor Extensores do Visual Studio
titleSuffix: ''
description: Saiba mais sobre o novo suporte de extensor para por monitor-reconhecimento disponível no Visual Studio de 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: db30c3d74a7742daa3c9cf7225bc2a38062dc6e4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660691"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Suporte a reconhecimento por Monitor Extensores do Visual Studio
Versões anteriores do Visual Studio de 2019 tinham seu contexto de reconhecimento DPI definido como o sistema sem suporte, em vez de reconhecimento de DPI (PMA) por monitor. Em execução no reconhecimento de sistema resultou em um visual degradado experiência sempre que o Visual Studio tinha que processar em vários monitores com fatores de escala diferente ou remota em máquinas com configurações de exibição diferentes, por exemplo, (diferente de (por exemplo, desfocadas fontes ou ícones) Windows dimensionamento).

O contexto de reconhecimento DPI do Visual Studio de 2019 é definido como PMA, quando o ambiente dá suporte a ele, permitindo que o Visual Studio para renderizar de acordo com a configuração da exibição em que ele está hospedado em vez de uma configuração de sistema único definida. Traduzindo, por fim, para uma interface do usuário sempre nítida para áreas de superfície que dão suporte ao modo PMA.

Consulte a [desenvolvimento de aplicativos de área de trabalho DPI alto no Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) documentação para obter mais informações sobre os termos e o cenário geral abordados neste documento.

## <a name="quickstart"></a>Guia de Início Rápido
- Verifique se o Visual Studio está em execução no modo PMA (consulte **PMA habilitando**)

- Validar sua extensão funciona corretamente em um conjunto de cenários comuns (consulte **teste suas extensões para problemas PMA**)

- Se você encontrar problemas, você pode usar as estratégias/recomendações discutidas neste documento para diagnosticar e corrigir esses problemas. Você também precisará adicionar o novo [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) pacote NuGet ao seu projeto para acessar as APIs necessárias.

## <a name="enabling-pma"></a>Habilitando PMA
Para habilitar PMA no Visual Studio, os requisitos a seguir precisam ser atendidos:
1)  10 de abril de 2018 do Windows Update (v1803 RS4) ou posterior
2)  .NET framework 4.8 RTM ou superior
3)  Visual Studio de 2019 com o ["Otimizar o processamento para telas com densidades de pixels diferente"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) opção habilitada

Quando esses requisitos forem atendidos, o Visual Studio habilitará automaticamente modo PMA entre o processo.

> [!NOTE]
> Conteúdo do Windows Forms no VS (por exemplo o navegador de propriedade) dará suporte PMA somente quando você tem a atualização n º 1 do Visual Studio de 2019.

## <a name="testing-your-extensions-for-pma-issues"></a>Teste suas extensões para problemas PMA

Visual Studio oficialmente dá suporte a estruturas de WPF, Windows Forms, Win32 e da interface do usuário de HTML/JS. Quando o Visual Studio será colocado no modo PMA, cada pilha de interface do usuário se comporta de forma diferente. Portanto, independentemente da estrutura de interface do usuário, é recomendável que uma aprovação de teste é executada para garantir que toda interface do usuário está em conformidade com o modo PMA.

É recomendável que você valide os seguintes cenários comuns:

1. Alterando o fator de escala de um ambiente de monitor único, enquanto o aplicativo está em execução *
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à alteração de DPI do Windows dinâmica

2. Encaixe/desencaixar um laptop em que um monitor conectado é definido como primário e o monitor conectado tem um fator de escala diferente que o laptop enquanto o aplicativo está em execução.
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à exibição, alteração de DPI, bem como manipulação exibe dinamicamente sendo adicionado ou removido

3. Ter vários monitores com fatores de escala diferente e mover o aplicativo, entre eles.
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à alteração DPI de exibição
    
4. Comunicação remota em um computador quando as máquinas locais e remotas têm fatores de escala diferente para o monitor principal.
    - Neste cenário ajuda a testar que a interface do usuário está respondendo à alteração de DPI do Windows dinâmica

Um bom teste preliminar para se sua interface do usuário pode ter problemas é se o código utiliza o *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper*, ou *VsUI::CDpiHelper* classes. Essas classes DpiHelper antigos só há suporte para reconhecimento de DPI do sistema e sempre não funcionarão corretamente quando o processo for PMA.

Um uso típico desses DpiHelpers se parecerá com:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

No exemplo anterior, um retângulo que representa os limites lógicos de uma janela é convertido em unidades de dispositivo para que ele pode ser passado para o método nativo MonitorFromPoint que espera as coordenadas do dispositivo para retornar um ponteiro de monitor precisos de volta.

### <a name="classes-of-issues"></a>Classes de problemas
Quando o modo PMA está habilitado para o Visual Studio, a interface do usuário foi possível replicar os problemas de várias maneiras comuns. A maioria, se não todos, esses problemas podem ocorrer em qualquer uma das estruturas de interface do usuário com suporte do Visual Studio. Além disso, esses problemas também podem acontecer quando uma parte da interface do usuário está sendo hospedada em cenários de dimensionamento de DPI de modo misto (consulte o Windows [documentação](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) para saber mais). 

#### <a name="win32-window-creation"></a>Criação da janela Win32
Ao criar o windows com CreateWindow() ou CreateWindowEx(), um padrão comum é criar a janela em coordenadas (0,0) (o canto superior/esquerdo da tela principal), em seguida, mova-o para sua posição final. No entanto, fazer isso pode fazer com que a janela disparar um DPI alterado mensagem ou evento, que pode disparar novamente outras mensagens de interface do usuário ou os eventos e eventualmente levar ao comportamento indesejado ou renderização.

#### <a name="wpf-element-placement"></a>Posicionamento de elemento do WPF
Ao mover elementos do WPF usando o antigo Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, as coordenadas do canto superior esquerdo podem não ser calculadas corretamente sempre que os elementos estão em um DPI não primário.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialização de tamanhos de elemento de interface do usuário ou posições
Quando o tamanho de interface do usuário ou a posição (se salvos como unidades de dispositivo) for restaurada em um contexto DPI diferente que o que ele foi armazenado no, ele será posicionado e dimensionado incorretamente. Isso acontece porque as unidades de dispositivo têm uma relação DPI inerente.

#### <a name="incorrect-scaling"></a>Dimensionamento incorreto
Elementos de interface do usuário criados na DPI primário serão dimensionado corretamente, no entanto, quando movido para uma exibição com um valor de DPIS diferente, eles não redimensione e assim, o seu conteúdo acaba sendo muito grande ou muito pequeno.

#### <a name="incorrect-bounding"></a>Delimitação incorreto
Da mesma forma, para o problema de colocação em escala, elementos de interface do usuário irá calcular seus limites corretamente em seu contexto DPI primário, no entanto, quando movido para um DPI não primário, eles não calculam corretamente os novos limites. Como tal, a janela de conteúdo acaba sendo muito grande ou muito pequeno em comparação com a hospedagem da interface do usuário, que resulta em espaço vazio ou recorte.

#### <a name="drag--drop"></a>Arrastar e soltar
Sempre que dentro de cenários DPI de modo misto (por exemplo, diferentes elementos interface do usuário de renderização em modos diferentes de reconhecimento DPI), arrastar e soltar coordenadas poderiam ser erro de cálculo, resultando na posição final soltar acaba incorreto.

#### <a name="out-of-process-ui"></a>Interface do usuário de fora do processo
Algumas interfaces do usuário é criado fora do processo e se o processo de criação externo estiver em um modo de reconhecimento DPI diferente que o Visual Studio, isso pode introduzir problemas de renderização anterior.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Controles dos Windows Forms, imagens ou layouts renderizados incorretamente
Não todo o conteúdo do Windows Forms suporte ao modo PMA. Como resultado, você poderá ver o problema com layouts incorretos de renderização ou dimensionamento. Nesse caso é uma solução possível renderizar explicitamente o conteúdo de Windows Forms no "Reconhecimento de sistema" DpiAwarenessContext (consulte a [forçando um controle em um DpiAwarenessContext específico](#forcing-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Controles dos Windows Forms ou windows não exibidos
Uma das principais causas para esse problema é que os desenvolvedores que tentarem reassociar um controle ou janela com um DpiAwarenessContext para uma janela com um DpiAwarenessContext diferente.

As imagens a seguir mostram o atual **padrão** restrições do sistema operacional Windows no domínio pai windows:

![Uma captura de tela do comportamento correto paternidade](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

> [!Note]
> Você pode alterar esse comportamento, definindo o comportamento de hospedagem de Thread (consulte a [DpiHostinBehaviour](https://docs.microsoft.com/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Como resultado, se você definir a relação pai-filho entre os modos sem suporte, ele falhará e o controle ou janela não pode ser renderizada conforme o esperado.

### <a name="diagnosing-issues"></a>Diagnosticando problemas
Há muitos fatores a considerar ao identificar problemas relacionados à PMA: 

1. Faz a interface do usuário ou a API espera lógico ou valores de dispositivo.
    - WPF UI e APIs normalmente usa valores lógicos (mas nem sempre)
    - Interface do usuário do Win32 e APIs normalmente usa valores de dispositivo

2. Em que os valores são provenientes?
    - Se receber valores de outra interface do usuário ou a API, é o dispositivo de passagem ou valores lógicos.
    - Se receber valores de várias fontes, todas as use/esperam que os mesmos tipos de valores ou conversões precisa ser misturadas e combinadas?

3. São constantes de interface do usuário em uso e de que forma eles estão?

4. É o thread no contexto correto de DPI para os valores está recebendo?
    - As alterações para habilitar a hospedagem de DPI misto geralmente devem colocar os caminhos de código no contexto certo, no entanto, o trabalho feito fora do fluxo de evento ou loop de mensagem principal pode executar no contexto errado de DPI.

5. O valores cruzar os limites de contexto do DPI?
    - Arrastar e soltar é uma situação comum em que as coordenadas podem cruzar os contextos DPI. Janela tenta fazer a coisa certa, mas em alguns casos, o host da interface do usuário talvez precise fazer o trabalho de conversão para garantir que os limites de contexto correspondente.

### <a name="pma-nuget-package"></a>Pacote do NuGet PMA
As novas bibliotecas DpiAwarness podem ser encontradas na [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) pacote do NuGet.

### <a name="recommended-tools"></a>Ferramentas recomendadas
As seguintes ferramentas podem ajudar a depurar problemas relacionados à PMA entre algumas das diferentes pilhas de interface do usuário com suporte do Visual Studio.

#### <a name="snoop"></a>Rastrear
Snoop é uma ferramenta de depuração de XAML que tem algumas funcionalidades adicionais que as ferramentas internas de XAML do Visual Studio não tem. Além disso, Snoop não precisa depurar ativamente o Visual Studio para ser capaz de exibir e ajustar sua UI WPF. As duas maneiras principais Snoop pode ser útil para diagnosticar problemas PMA é para validar as coordenadas de posicionamento lógico ou limites de tamanho, e para validar a interface do usuário tem o direito DPI.
 
#### <a name="visual-studio-xaml-tools"></a>Ferramentas do Visual Studio XAML
Como Snoop, as ferramentas XAML no Visual Studio podem ajudar a diagnosticar problemas PMA. Depois que um provável culpado for encontrado, você pode definir pontos de interrupção e usar a janela Live Visual Tree, bem como as janelas de depuração, para inspecionar os limites da interface do usuário e DPI atual.

## <a name="strategies-for-fixing-pma-issues"></a>Estratégias para corrigir problemas PMA
### <a name="replacing-dpihelper-calls"></a>A substituição das chamadas de DpiHelper
Na maioria dos casos, corrigindo problemas de interface do usuário em modo PMA se resume a substituição das chamadas em código gerenciado e o antigo *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* e *Microsoft.VisualStudio.PlatformUI.DpiHelper*classes com chamadas para o novo *Microsoft.VisualStudio.Utilities.DpiAwareness* classe auxiliar. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Para código nativo, ele envolvem substituindo chamadas para o antigo *VsUI::CDpiHelper* classe com chamadas para o novo *VsUI::CDpiAwareness* classe. 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

As novas classes DpiAwareness e CDpiAwareness oferecem a mesma unidade de auxiliares de conversão como as classes DpiHelper, mas não requerem um parâmetro de entrada adicional: o elemento de interface do usuário a ser usado como uma referência para a operação de conversão. É importante observar que os auxiliares de colocação em escala de imagem não existe no novo auxiliares de DpiAwareness/CDpiAwareness e, se necessário, o [ImageService](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog?view=vs-2019) deve ser usado em vez disso.

A classe DpiAwareness gerenciada oferece auxiliares para elementos visuais do WPF, controles de formulários do Windows e Win32 HWNDs e HMONITORs (ambos na forma de IntPtrs), enquanto os nativo CDpiAwareness ofertas HWND e HMONITOR auxiliares da classe.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Caixas de diálogo do Windows Forms, windows ou controles exibidos no DpiAwarenessContext errado
Mesmo após uma paternidade bem-sucedida do windows com DpiAwarenessContexts diferentes (devido ao comportamento de padrão do Windows), usuários ainda poderão ver problemas de dimensionamento como janelas com escala diferente de DpiAwarenessContexts diferente. Como resultado, os usuários podem ver alinhamento/desfocado texto ou problemas da interface do usuário da imagem.

A solução é definir o escopo de DpiAwarenessContext correto para todas as janelas e controles no aplicativo.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Caixas de diálogo de nível superior de modo misto (TLMM)
Ao criar janelas de nível superior, como caixas de diálogo modais, é importante garantir que o thread está no estado correto antes da janela (e seu identificador) que está sendo criado. O thread pode ser colocado no reconhecimento de sistema, usando o auxiliar de CDpiScope no formato nativo ou gerenciado o auxiliar DpiAwareness.EnterDpiScope no. (TLMM geralmente deve ser usada em caixas de diálogo de não-WPF/windows.)

### <a name="child-level-mixed-mode-clmm"></a>Nível filho de modo misto (CLMM)
Por padrão, janelas filho recebem o DPI reconhecimento contexto do thread atual se criado sem um pai ou o contexto de reconhecimento DPI do pai quando criado com um pai. Para criar um filho com um contexto de reconhecimento DPI diferente de seu pai, o thread pode ser colocado no contexto de reconhecimento de DPI desejado. Em seguida, o filho pode ser criado sem um pai e seus pais modificado manualmente para a janela pai.

#### <a name="clmm-issues"></a>Problemas CLMM
Grande parte do trabalho de cálculo de interface do usuário ocorre como parte da principal mensagens loop ou evento cadeia já deve estar executando no contexto certo de reconhecimento DPI. No entanto, se coordenada ou cálculos de dimensionamento são feitos fora desses fluxos de trabalho principais (como durante uma tarefa de tempo ocioso, ou fora do thread de interface do usuário, o contexto atual de reconhecimento DPI pode estar incorreto levando a localização errada da interface do usuário ou problemas de dimensionamento incorretamente. Colocando o thread no estado correto para a interface do usuário trabalho geralmente corrige o problema.
 
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
```cpp
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

> [!NOTE]
> Visual Studio suporta apenas PerMonitorV2 reconhecimento, portanto, o valor de enumeração PerMonitor convertida para o valor de Windows do DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="forcing-a-control-into-a-specific-dpiawarenesscontext"></a>Forçando um controle em um DpiAwarenessContext específico
Interface de usuário herdado que não está sendo atualizado para dar suporte PMA modo, talvez ainda precise de pequenos ajustes para o trabalho enquanto o Visual Studio está em execução no modo PMA. Uma correção de tal envolve a certeza de que a interface do usuário está sendo criado no DpiAwarenessContext à direita. Para forçar a interface do usuário em um determinado DpiAwarenessContext, você pode inserir um escopo DPI com o código a seguir:

C#:
```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

C++:
```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Forçar o DpiAwarenessContext funciona somente em não - interface do usuário WPF e o nível superior caixas de diálogo do WPF. Quando criar UI WPF que está hospedado dentro de janelas de ferramentas ou designers, assim que o conteúdo é inserido na árvore WPF UI, ele obtém convertido para o processo atual DpiAwarenessContext.

## <a name="known-issues"></a>Problemas conhecidos
### <a name="windows-forms"></a>Windows Forms

Para otimizar os novos cenários de modo misto, o Windows Forms alterado como ele cria controles e janelas sempre que seu pai não foi explicitamente definido. Anteriormente, controles sem um pai explícito usado um "estacionamento janela interno" como um pai temporário para o controle ou janela que está sendo criada. 

Antes do .NET 4.8, havia um único "de estacionamento janela" que obtém seu DpiAwarenessContext do contexto de reconhecimento DPI de thread atual no momento da criação da janela. Qualquer controle órfãos herda o mesmo DpiAwarenessContext como a janela de estacionamento quando o identificador do controle é criado e deve ser reassociado ao pai final/esperado pelo desenvolvedor do aplicativo. Isso faria com que falhas de medição de tempo se a "janela de estacionamento" tinha um DpiAwarenessContext maior que a janela pai final.

A partir do .NET 4.8, agora há uma "estacionamento janela" para cada DpiAwarenessContext foi encontrado. A principal diferença é que o DpiAwarenessContext usada para o controle em cache quando o controle é criado, não quando o identificador é criado. Isso significa que o comportamento geral do final é o mesmo, mas pode ativar o que costumava ser um problema de tempo em um problema consistente. Ele também oferece ao desenvolvedor de aplicativos mais comportamento determinístico para escrever seu código de interface do usuário e escopo-la corretamente.
