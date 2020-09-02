---
title: Como exibir informações de rastreamento do WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c9642902bf334ce83f95a9113059683f183c6116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537948"
---
# <a name="how-to-display-wpf-trace-information"></a>Como exibir informações de acompanhamento WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] pode receber informações de rastreamento de depuração de aplicativos do WPF e exibir essas informações na janela de **Saída**. Para exibir informações de rastreamento de depuração, o rastreamento do WPF deve estar habilitado.  
  
 Você pode habilitar o rastreamento do WPF no arquivo App.config ou programaticamente usando a classe <xref:System.Diagnostics.PresentationTraceSources>. Uma forma mais fácil de habilitar o rastreamento do WPF é usando a janela **Opções**. O rastreamento do WPF para aplicativos Web não tem suporte.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar ou personalizar as informações de rastreamento do WPF  
  
1. No menu **Ferramentas**, selecione **Opções**.  
  
2. Na caixa de diálogo **Opções**, na caixa à esquerda, abra o nó **Depuração**.  
  
3. Em **Depuração**, clique em **Janela de Saída**.  
  
4. Em **Configurações Gerais de Saída**, selecione **Todas as saídas da depuração**.  
  
5. Na caixa à direita, procure **Configurações de Rastreamento de WPF**.  
  
6. Abra o nó **Configurações de Rastreamento de WPF**.  
  
7. Em **Configurações de Rastreamento de WPF**, clique na categoria de configurações que você deseja habilitar (por exemplo, **Associação de Dados**).  
  
     Um controle de lista suspensa aparece na coluna Configurações ao lado de **Associação de Dados** ou de qualquer categoria que você tiver clicado.  
  
8. Clique na lista suspensa e selecione o tipo de informações de rastreamento que você quer consultar: **Tudo**, **Crítico**, **Erro**, **Aviso**, **Informações**, **Detalhado** ou **ActivityTracing**.  
  
     **Crítico** habilita o rastreamento apenas de eventos Críticos.  
  
     **Erro** habilita o rastreamento de eventos Críticos e de Erro.  
  
     **Aviso** habilita o rastreamento de eventos Críticos, de Erro e Aviso.  
  
     **Informações** habilita o rastreamento de eventos Críticos, de Erro, de Aviso e de Informações.  
  
     **Detalhado** habilita o rastreamento de eventos Críticos, de Erro, de Aviso, de Informações e Detalhado.  
  
     **ActivityTracing** habilita o rastreamento dos eventos Parar, Iniciar, Suspender, Transferir e Retomar.  
  
     Para obter mais informações sobre o significado desses níveis de informações de rastreamento, consulte <xref:System.Diagnostics.SourceLevels>.  
  
9. Clique em **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Para desabilitar as informações de rastreamento do WPF  
  
1. No menu **Ferramentas**, selecione **Opções**.  
  
2. Na caixa de diálogo **Opções**, na caixa à esquerda, abra o nó **Depuração**.  
  
3. Em **Depuração**, clique em **Janela de Saída**.  
  
4. Na caixa à direita, procure **Configurações de Rastreamento de WPF**.  
  
5. Abra o nó **Configurações de Rastreamento de WPF**.  
  
6. Em **Configurações de Rastreamento de WPF**, clique na categoria de configurações que você deseja habilitar (por exemplo, **Associação de Dados**).  
  
     Um controle de lista suspensa aparece na coluna Configurações ao lado de **Associação de Dados** ou de qualquer categoria que você tiver clicado.  
  
7. Clique na lista suspensa e selecione **Desativar**.  
  
8. Clique em **OK**.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurando WPF](../debugger/debugging-wpf.md)
