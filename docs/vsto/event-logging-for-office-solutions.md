---
title: Log de eventos para soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 480a355ee2af321341c54b90edcc582d49102186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951925"
---
# <a name="event-logging-for-office-solutions"></a>Log de eventos para soluções do Office
  Você pode usar o Visualizador de eventos no Windows para ver as mensagens de exceção que são capturadas pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando você instala ou desinstala as soluções do Office. Você pode usar essas mensagens do agente de log de eventos para resolver problemas de instalação e implantação.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Ler o log de eventos
 Abra **Visualizador de eventos** e filtre os eventos que você deseja ver.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Para ler o log de eventos no Windows Server 2003 e no Windows XP

1. No painel de controle, abra **Ferramentas administrativas**.

2. Iniciar **Visualizador de eventos**.

3. Na lista de logs de eventos, selecione **aplicativo**.

4. No menu **Exibir** , clique em **Filtrar**.

5. Na lista **origem do evento** , selecione **VSTO 4,0**.

6. Para eventos de instalação, na caixa **ID do evento** , digite **4096**.

7. Clique em **OK** para ver a exibição filtrada.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Para ler o log de eventos no Windows 7, no Windows Vista e no Windows Server 2008

1. No painel de controle, abra **Ferramentas administrativas**.

2. Iniciar **Visualizador de eventos**.

3. Expanda **logs do Windows**.

4. Na lista de logs de eventos, selecione **aplicativo**.

5. No menu **Ação**, clique em **Filtrar Log Atual**.

6. Na lista **origem do evento** , selecione **VSTO 4,0**.

7. Para eventos de instalação, na caixa **ID do evento** , digite **4096**.

8. Clique em **OK** para ver a exibição filtrada.

   O Visualizador de eventos inclui as seguintes informações:

- O local do manifesto de implantação para a solução.

- Uma mensagem que descreve a causa do erro ou da exceção.

  Essas mensagens de exceção podem ajudá-lo a determinar o motivo de um problema de instalação, como um certificado não confiável, um local de documento não confiável ou um manifesto de implantação inválido.

  Depois que uma solução do Office é desinstalada, as mensagens de exceção permanecem no log de eventos.

  Para mostrar ou registrar mensagens de exceção quando uma solução do Office estiver em execução, consulte [depurar projetos do Office](../vsto/debugging-office-projects.md) e [depurar projetos do Office](../vsto/debugging-office-projects.md).

### <a name="localization"></a>Localização
 O idioma da mensagem de exceção é determinado pelo Ferramentas do Visual Studio para a linguagem de tempo de execução do Office. Por exemplo, se o computador do usuário final tiver o pacote de idiomas japonês instalado, a mensagem de exceção será gravada no log de eventos em Japonês.

## <a name="disable-the-event-logger"></a>Desabilitar o agente de log de eventos
 Por padrão, o agente de log de eventos é habilitado quando você instala ou desinstala as soluções do Office. Você pode desabilitar o agente de log de eventos definindo a variável de ambiente VSTO_EVENTLOGDISABLED como "1" (uma).

### <a name="to-disable-the-event-log"></a>Para desabilitar o log de eventos

1. No painel de controle, abra **sistema**.

2. Na guia **avançado** , clique em **variáveis de ambiente**.

3. No painel **variáveis do sistema** , clique em **novo**.

4. Na caixa de diálogo **nova variável do sistema** , digite **VSTO_EVENTLOGDISABLED** na caixa **nome da variável** .

5. Na caixa **valor da variável** , digite **1**.

6. Clique em **OK**.

## <a name="see-also"></a>Confira também
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Solucionar problemas de implantação de solução do Office](../vsto/troubleshooting-office-solution-deployment.md)
