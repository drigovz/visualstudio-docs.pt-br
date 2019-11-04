---
title: 'Como: Depurar fluxos de trabalho baseados em ASP.NET (Herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668667"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Como: Depurar de fluxos de trabalho baseados no ASP.NET (herdado)
Este tópico descreve como depurar aplicativos baseadas em [!INCLUDE[vstecasp](../includes/vstecasp-md.md)][!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] em [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado.

 Você pode depurar fluxos de trabalho herdados que são iniciados no ASP.NET ou em fluxos de trabalho herdados que são publicados como um serviço Web anexando o processo no qual o fluxo de trabalho é hospedado.

### <a name="to-debug-an-aspnet-based-workflow"></a>Para depurar um fluxo de trabalho ASP.NET-based

1. Habilite a depuração para o aplicativo ASP.NET definindo **Debug = true** no arquivo Web. config.

2. Defina a biblioteca de fluxo de trabalho como o projeto de inicialização, e pontos de interrupção no fluxo de trabalho.

3. Insira a URL da página da Web padrão na opção do projeto de fluxo de trabalho Propriedades de **depurador** **Iniciar navegador com a caixa de texto URL externa** .

4. Selecione **anexar ao processo** no menu **depurar** .

5. Selecione o processo a ser anexado na lista de **processos disponíveis** .

     Para anexar w3wp.exe, ao webdev.webserver, ou o processo de aspnet_wp em que o fluxo de trabalho é hospedado.

6. Clique em **selecionar** ao lado da caixa de texto **anexar a** .

     A caixa de diálogo **Selecionar tipo de código** é exibida.

7. Selecione **depurar esses tipos de código** e selecione **fluxo de trabalho**.

8. Clique em **OK**.

9. Clique em **Anexar**.

10. Abra a página da Web padrão em um navegador e inicie o fluxo de trabalho.

## <a name="see-also"></a>Consulte também
 [Invocar o depurador do Visual Studio para [How de Windows Workflow Foundation (Herdado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) para: Definir pontos de interrupção em fluxos de trabalho (herdados)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [depurar fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)