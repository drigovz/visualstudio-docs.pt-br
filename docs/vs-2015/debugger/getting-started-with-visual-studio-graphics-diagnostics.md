---
title: Introdução com Diagnóstico de Gráficos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704702"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Introdução ao Diagnóstico de Gráficos do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesta seção, você se preparará para usar Diagnóstico de Gráficos pela primeira vez e, em seguida, capturará quadros de um aplicativo do Direct3D e os examinará no analisador de gráficos.

## <a name="requirements"></a>Requisitos
 Para usar Diagnóstico de Gráficos no Visual Studio 2015, você deve ter uma destas edições:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Comunidade do Visual Studio 2015

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Pré-requisitos do Windows 10
 As *ferramentas gráficas* de recursos opcionais do Windows fornecem a infraestrutura de captura e reprodução exigida pelo diagnóstico de gráficos no Windows 10.

 Para obter informações sobre como instalar ferramentas de gráficos, consulte [instalar ferramentas de gráficos para Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Pré-requisitos de Windows 8.1
 O SDK (Software Development Kit) do Windows para Windows 8.1 fornece a infraestrutura de captura e reprodução necessária para Diagnóstico de Gráficos no Windows 8.1 e dá suporte ao desenvolvimento para Windows 8.1 e para o Windows 8.

 [Baixe o SDK (Software Development Kit) do Windows para Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Para usar um computador de reprodução remota que executa o Windows 10 em um computador de desenvolvimento executando o Windows 8.1, você deve instalar o SDK do Windows 10 no computador de desenvolvimento e o recurso ferramentas gráficas opcionais no computador de reprodução.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalar ferramentas de gráficos para Windows 10
 No Windows 10, a infra-estrutura de Diagnóstico de Gráficos é fornecida por um recurso opcional do Windows chamado *ferramentas de gráficos*. Esse recurso é necessário para capturar e reproduzir informações de gráficos no Windows 10, independentemente de o aplicativo ser capturado ter como destino uma versão anterior do Windows ou qual versão do Direct3D ela usa. Você pode optar por instalar o recurso de ferramentas de gráficos antecipadamente; caso contrário, ele será instalado sob demanda na primeira vez que você iniciar uma sessão de Diagnóstico de Gráficos do Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Para instalar as ferramentas de gráficos para Windows 10

1. No menu **Iniciar** , escolha **configurações**. A caixa de diálogo **configurações** é exibida.

2. Na caixa de diálogo **configurações** , escolha **sistema**e, em seguida, selecione **aplicativos instalados** na lista de configurações do sistema.

3. No lado direito da caixa de diálogo **configurações** , escolha **gerenciar recursos opcionais** em **aplicativos e recursos instalados**. A caixa de diálogo **gerenciar recursos opcionais** é exibida.

4. Na caixa de diálogo **gerenciar recursos opcionais** , escolha **Adicionar um recurso**. É exibida uma lista de recursos opcionais que você pode instalar.

5. Selecione **ferramentas de gráficos** na lista de recursos e escolha **instalar**.

   O recurso ferramentas de gráficos também é instalado automaticamente quando você instala o SDK do Windows 10.

> [!TIP]
> O recurso ferramentas gráficas opcionais do Windows 10 fornece funcionalidade leve de captura e reprodução, como a **dxcap.exe**do programa de captura de linha de comando, que pode ser usado em cenários de suporte, teste e diagnóstico em computadores em que as ferramentas de desenvolvedor não estão instaladas. Para obter mais informações, consulte o tópico [ferramenta de captura de linha de comando](../debugger/command-line-capture-tool.md) .

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Usando Diagnóstico de Gráficos pela primeira vez
 Agora que você tem tudo o que precisa, você está pronto para começar a usar Diagnóstico de Gráficos. Basta seguir estas etapas.

### <a name="1---create-a-direct3d-app"></a>1-criar um aplicativo do Direct3D
 Se você já tem seu próprio aplicativo do Direct3D para explorar Diagnóstico de Gráficos, ótimo! Caso contrário, você pode usar um dos exemplos de Direct3D disponíveis na Galeria de códigos.

- Para experimentar Diagnóstico de Gráficos com o Direct3D 12 no Windows 10 usando o Visual Studio 2015, experimente o [exemplo do Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) para Windows 10.

- Para experimentar Diagnóstico de Gráficos com o Direct3D 11 no Windows 10 ou Windows 8.1, você pode usar os modelos de projeto do **aplicativo DirectX (Windows universal)** ou  **aplicativo DirectX (Windows 8.1)** . Ou, para algo mais interessante, experimente o [exemplo de jogo de labirinto de mármore DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) para Windows 8.1.

  Verifique se você pode compilar o aplicativo antes de prosseguir.

### <a name="2---start-a-graphics-diagnostics-session"></a>2-iniciar uma sessão de Diagnóstico de Gráficos
 Agora você está pronto para iniciar sua primeira sessão de diagnóstico de gráficos. No Visual Studio, no menu principal, escolha **depurar, gráficos, iniciar diagnóstico**ou apenas pressione **ALT + F5**. Isso inicia seu aplicativo em Diagnóstico de Gráficos e exibe as janelas de sessão de diagnóstico no Visual Studio.

> [!IMPORTANT]
> Se você estiver executando seu aplicativo no Windows 10 e ainda não tiver instalado o recurso de ferramentas gráficas opcionais, você será solicitado a fazer isso agora. Você deve instalá-lo antes de poder usar Diagnóstico de Gráficos no Windows 10.

### <a name="3---capture-frames"></a>3-capturar quadros
 Você está pronto para capturar quadros assim que seu aplicativo é iniciado.

##### <a name="to-capture-single-frames"></a>Para capturar quadros únicos

- No Visual Studio, escolha o botão **capturar quadro** na barra de ferramentas de gráficos ou na janela sessão de diagnóstico. Ou, se seu aplicativo tiver foco, basta pressionar **imprimir tela**.

##### <a name="to-capture-a-sequence-of-frames"></a>Para capturar uma sequência de quadros

- No Visual Studio, na janela sessão de diagnóstico, defina os **quadros a serem capturados** para o número de quadros que você deseja capturar em sequência e, em seguida, Capture a sequência usando qualquer um dos métodos descritos acima para capturar quadros únicos.

   Para capturar quadros únicos novamente, defina os **quadros para captura** `1` .

  Quando você terminar de capturar quadros, basta sair do aplicativo ou escolher o botão **parar** na barra de ferramentas de gráficos ou na janela sessão de diagnóstico.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 – examinar os quadros capturados no analisador de gráficos
 Agora você está pronto para examinar os quadros que acabou de capturar. Para começar a analisar um quadro, escolha o número do quadro que você deseja examinar na janela sessão de diagnóstico. Isso abre o quadro no **analisador de gráficos**, no qual você pode usar as ferramentas de diagnóstico de gráficos para examinar como seu aplicativo usa o Direct3D para rastrear problemas de renderização ou usar a ferramenta de **análise de quadros** para entender seu desempenho.

 Se você selecionou o quadro incorreto na janela sessão de diagnóstico ou deseja examinar um quadro diferente, poderá selecionar um novo no analisador de gráficos. Na guia **destino de renderização** da janela de log de gráficos, sob a imagem de destino de renderização, expanda a **lista de quadros** e escolha um quadro diferente para examinar.

 Para saber mais sobre como usar as ferramentas do analisador de gráficos juntas, consulte os [exemplos](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Consulte Também
 [Elementos gráficos do Direct3D 12](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
