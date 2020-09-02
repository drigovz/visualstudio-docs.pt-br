---
title: 'Como: usar a janela Modules | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696122"
---
# <a name="how-to-use-the-modules-window"></a>Como usar a janela Módulos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
> Esse recurso não está disponível para depuração do SQL ou script.  
  
 A janela **módulos** lista as DLLs e o exe que são usados pelo seu programa e mostra informações relevantes para cada um.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Para exibir a janela Módulos no modo de interrupção ou no modo de execução  
  
- No menu **depurar** , escolha **Windows**e clique em **módulos**.  
  
     Por padrão, a janela **Módulos** classifica os módulos pela ordem de carregamento. No entanto, você pode escolher classificar por qualquer coluna.  
  
### <a name="to-sort-by-any-column"></a>Para classificar por qualquer coluna  
  
- Clique no botão na parte superior da coluna.  
  
     Você pode carregar símbolos ou especificar um caminho de símbolo na janela **módulos** usando o menu de atalho.  
  
## <a name="loading-symbols"></a>Carregando símbolos  
 Na janela **módulos** , você pode ver quais módulos têm símbolos de depuração carregados. Essas informações são exibidas na coluna **status do símbolo** . Se o status for **ignorado, loadingCannot localizar ou abrir o arquivo PDB**ou **carregar desabilitado pela configuração incluir/excluir**, você poderá direcionar o depurador para baixar símbolos dos servidores de símbolos públicos da Microsoft ou para carregar símbolos de um diretório de símbolos no seu computador. Para obter mais informações, consulte [especificar símbolo (. pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Para carregar símbolos manualmente  
  
1. Na janela **módulos** , clique com o botão direito do mouse em um módulo para o qual os símbolos não foram carregados.  
  
2. Aponte para **carregar símbolos de** e clique em **servidores de símbolos** ou **caminho de símbolo**da Microsoft.  
  
#### <a name="to-change-symbol-load-settings"></a>Para alterar as configurações de carregamento do símbolo  
  
1. Na janela **Módulos**, clique com o botão direito do mouse direito em qualquer módulo.  
  
2. Clique em **configurações de símbolo**.  
  
     Agora você pode alterar as configurações de carregamento de símbolo, conforme descrito em [especificar locais de símbolo e comportamento de carregamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Para alterar o comportamento de carregamento do símbolo para um módulo específico  
  
1. Na janela **Módulos**, clique com o botão direito do mouse no módulo.  
  
2. Aponte para **configurações de carregamento de símbolo automático** e, em seguida, clique em **sempre carregar manualmente** ou **padrão**. As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Interrupção da execução](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar os arquivos de origem e símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
