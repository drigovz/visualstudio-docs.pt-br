---
title: Comandos importantes para filtros de serviço de idioma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707620"
---
# <a name="important-commands-for-language-service-filters"></a>Comandos importantes para filtros do serviço de linguagem
Se você quiser criar um filtro de serviço de idioma totalmente caracterizado, considere manusear os seguintes comandos. A lista completa de identificadores <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> de comando é definida na enumeração para código gerenciado e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no arquivo de cabeçalho Stdidcmd.h para código não gerenciado. Você pode encontrar o arquivo Stdidcmd.h no *caminho de instalação do Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Comandos para lidar

> [!NOTE]
> Não é obrigatório filtrar para cada comando na tabela a seguir.

|Comando|Descrição|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado quando o usuário clica com o botão direito do mouse. Este comando indica que é hora de fornecer um menu de atalho. Se você não lidar com esse comando, o editor de texto fornecerá um menu de atalho padrão sem nenhum comando específico do idioma. Para incluir seus próprios comandos neste menu, manuseie o comando e exiba um menu de atalho você mesmo.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente enviado quando o usuário digita CTRL+J. Ligue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> método para mostrar a caixa de conclusão da declaração.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado quando o usuário digita um caractere. Monitore este comando para determinar quando um caractere de gatilho é digitado e para fornecer conclusão de declaração, dicas de método e marcadores de texto, como coloração de sintaxe, correspondência de chaves e marcadores de erro. Ligue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> método para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> o preenchimento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> da declaração e o método sobre as dicas do método para obter. Para suportar marcadores de texto, monitore este comando para determinar se o caractere que está sendo digitado requer que você atualize seus marcadores.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado quando o usuário digita a tecla Enter. Monitore este comando para determinar quando descartar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> uma janela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>de ponta do método chamando o método no . Por padrão, a exibição de texto lida com este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado quando o usuário digita a tecla Backspace. Monitore para determinar quando descartar uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> janela de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>ponta do método chamando o método no . Por padrão, a exibição de texto lida com este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado a partir de um menu ou uma chave de atalho. Ligue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> método para atualizar a janela de ponta com as informações do parâmetro.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado quando o usuário paira sobre uma variável ou posiciona o cursor em uma variável e seleciona **Informações Rápidas** do **IntelliSense** no menu **Editar.** Retorne o tipo da variável em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> uma ponta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>chamando o método no . Se a depuração estiver ativa, a ponta também deve mostrar o valor da variável.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente enviado quando o usuário digita CTRL+SPACEBAR. Este comando diz ao serviço <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>idiomas para chamar o método no .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado de um menu, tipicamente **Seleção de comentários** ou **Seleção de Não Comentar** de **Avançado** no menu **Editar.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica que o usuário deseja comentar o texto selecionado; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que o usuário deseja descomentar o texto selecionado. Esses comandos só podem ser implementados pelo serviço de idiomas.|

## <a name="see-also"></a>Confira também
- [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
