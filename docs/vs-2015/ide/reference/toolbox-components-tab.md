---
title: Caixa de ferramentas, Guia Componentes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661567"
---
# <a name="toolbox-components-tab"></a>Caixa de Ferramentas, Guia Componentes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe os componentes que podem ser adicionados a designers [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Além dos componentes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] incluídos no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], como os componentes <xref:System.Messaging.MessageQueue> e <xref:System.Diagnostics.EventLog>, é possível adicionar seus próprios componentes ou os componentes de terceiros a essa guia. Para obter mais informações, consulte [Como manipular guias da caixa de ferramentas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Para exibir essa guia, no menu **Exibir**, selecione **Caixa de ferramentas**. Na **Caixa de ferramentas**, selecione a guia **Componentes**.

 **BackgroundWorker** Cria uma instância de componente `System.ComponentModel.BackgroundWorker` que pode executar uma operação em um thread separado e dedicado.

 **DirectoryEntry** Cria uma instância de componente <xref:System.DirectoryServices.DirectoryEntry> que encapsula um nó ou objeto na hierarquia de Active Directory e pode ser usada para interagir com provedores de serviços Active Directory.

 **DirectorySearcher** Cria uma instância de componente <xref:System.DirectoryServices.DirectorySearcher> que você pode usar para executar consultas no Active Directory.

 **ErrorProvider** Cria um `System.Windows.Forms.ErrorProvider` instância de componente, que indica ao usuário final que um controle em um formulário tem um erro associado a ele.

 **Log de eventos** Cria uma instância de componente <xref:System.Diagnostics.EventLog> que você pode usar para interagir com logs de eventos do sistema e personalizados, incluindo a gravação de eventos em um log e a leitura de dados de log. Para obter mais informações, consulte [Introdução ao componente EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Cria uma instância de componente <xref:System.IO.FileSystemWatcher> que você pode usar para monitorar as alterações em qualquer diretório ou arquivo ao qual você tenha acesso. Para obter mais informações, consulte [Como configurar as instâncias do componente FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Cria uma instância de componente `System.Windows.Forms.HelpProvider` que fornece ajuda pop-up ou online para controles.

 **ImageList** Cria uma instância de componente `System.Windows.Forms.ImageList` que fornece métodos para gerenciar uma coleção de objetos `System.Drawing.Image`.

 **MessageQueue** Cria uma instância de componente <xref:System.Messaging.MessageQueue> que você pode usar para interagir com filas de mensagens, incluindo a leitura de mensagens de e a gravação de mensagens em filas, processamento de transações e execução de tarefas de administração de fila. Para obter mais informações, consulte [Usando componentes de mensagens](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Cria uma instância de componente <xref:System.Diagnostics.PerformanceCounter> que você pode usar para interagir com contadores de desempenho do Windows, incluindo a criação de novas categorias e instâncias, a leitura de valores de contadores e a execução de cálculos em dados do contador. Para obter mais informações, consulte [Monitorando limites de desempenho](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Processo** do Cria uma instância de componente <xref:System.Diagnostics.Process> que você pode usar para parar, iniciar e manipular os dados associados aos processos em seu sistema. Para obter mais informações, consulte [Monitorando e gerenciando processos do Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Cria uma instância de componente de `System.IO.Ports.SerialPort` que fornece e/s síncrona e orientada por evento, acesso a Estados de PIN e de interrupção e acesso às propriedades do driver serial.

 **ServiceController** Cria uma instância de componente <xref:System.ServiceProcess.ServiceController> que você pode usar para manipular os serviços existentes, incluindo iniciar e interromper serviços e enviar comandos para eles. Para obter mais informações, consulte [Monitorando serviços Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Temporizador** Cria uma instância de componente <xref:System.Windows.Forms.Timer> que você pode usar para adicionar funcionalidade baseada em tempo a seus aplicativos baseados no Windows. Para obter mais informações, consulte [Componente de temporizador](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> Também há um <xref:System.Timers.Timer> baseado em sistema que pode ser adicionado à **Caixa de ferramentas**. Esse <xref:System.Timers.Timer> é otimizado para aplicativos de servidor e o <xref:System.Windows.Forms.Timer> do Windows Forms é mais adequado para uso no Windows Forms.

## <a name="see-also"></a>Veja também
 [Programando a programação com componentes de](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [componente](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) [ferramentas](../../ide/reference/toolbox.md) de programação [escolher itens da caixa de ferramentas (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
