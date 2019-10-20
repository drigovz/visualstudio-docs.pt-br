---
title: Caixa de Ferramentas, Guia Componentes
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd9c6bf4d24a681c426a20f490dba2cc1d5080fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644602"
---
# <a name="toolbox-components-tab"></a>Caixa de Ferramentas, guia Componentes

Exibe os componentes que podem ser adicionados a designers do Visual Basic e C# do Windows Forms. Além dos componentes .NET incluídos no Visual Studio, como os componentes <xref:System.Messaging.MessageQueue> e <xref:System.Diagnostics.EventLog>, é possível adicionar seus próprios componentes ou componentes de terceiros a essa guia.

Para exibir essa guia, abra um designer do Windows Forms. Selecione **Modo de Exibição** > **Caixa de Ferramentas**. Em **Caixa de ferramentas**, selecione a guia **Componentes**.

## <a name="components"></a>Componentes

**BackgroundWorker**

Cria uma instância do componente <xref:System.ComponentModel.BackgroundWorker> que pode executar uma operação em um thread separado e dedicado. Para obter mais informações, confira [Componente BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Cria uma instância do componente <xref:System.DirectoryServices.DirectoryEntry>, que encapsula um nó ou um objeto na hierarquia do Active Directory e pode ser usada para interagir com provedores de serviços do Active Directory.

**DirectorySearcher**

Cria uma instância do componente <xref:System.DirectoryServices.DirectorySearcher>, que pode ser usada para executar consultas no Active Directory.

**ErrorProvider**

Cria uma instância do componente <xref:System.Windows.Forms.ErrorProvider>, que indica para o usuário final que um controle em um formulário tem um erro associado a ele. Para obter mais informações, confira [Componente ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Cria uma instância do componente <xref:System.Diagnostics.EventLog>, que pode ser usada para interagir com logs do sistema e de eventos personalizados, incluindo a gravação de eventos em um log e a leitura dos dados de log.

**FileSystemWatcher**

Cria uma instância do componente <xref:System.IO.FileSystemWatcher>, que pode ser usada para monitorar alterações em um diretório ou arquivo ao qual você tem acesso.

**HelpProvider**

Cria uma instância do componente <xref:System.Windows.Forms.HelpProvider> que fornece ajuda pop-up ou online para controles. Para obter mais informações, confira [Componente HelpProvider](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Cria uma instância do componente <xref:System.Windows.Forms.ImageList> que fornece métodos para gerenciar uma coleção de objetos <xref:System.Drawing.Image>. Para obter mais informações, confira [Componente ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Cria uma instância do componente <xref:System.Messaging.MessageQueue>, que pode ser usada para interagir com filas de mensagens, incluindo a leitura e gravação de mensagens em filas, o processamento de transações e a realização de tarefas de administração de fila.

**PerformanceCounter**

Cria uma instância do componente <xref:System.Diagnostics.PerformanceCounter>, que pode ser usada para interagir com contadores de desempenho do Windows, incluindo a criação de novas categorias e instâncias, a leitura de valores de contadores e a execução de cálculos nos dados do contador.

**Process**

Cria uma instância do componente <xref:System.Diagnostics.Process>, que pode ser usada para interromper, iniciar e manipular os dados associados a processos no sistema.

**SerialPort**

Cria uma instância do componente <xref:System.IO.Ports.SerialPort> que fornece E/S síncrona e controlada por evento, acesso ao PIN e estados de fixação e interrupção e acesso às propriedades do driver serial.

**ServiceController**

Cria uma instância do componente <xref:System.ServiceProcess.ServiceController>, que pode ser usada para manipular serviços existentes, incluindo a inicialização e a interrupção de serviços e o envio de comandos para eles.

**Timer**

Cria uma instância do componente <xref:System.Windows.Forms.Timer>, que pode ser usada para adicionar funcionalidade baseada em tempo aos aplicativos baseados no Windows. Para obter mais informações, confira [Componente Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Também há um <xref:System.Timers.Timer> baseado em sistema que pode ser adicionado à **Caixa de ferramentas**. Esse <xref:System.Timers.Timer> é otimizado para aplicativos de servidor e o <xref:System.Windows.Forms.Timer> do Windows Forms é mais adequado para uso no Windows Forms.

## <a name="see-also"></a>Consulte também

- [Controles a serem usados no Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Escolher itens da Caixa de Ferramentas, componentes do WPF](choose-toolbox-items-wpf-components.md)
- [Caixa de Ferramentas](../../ide/reference/toolbox.md)