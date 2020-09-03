---
title: 'Como: Depurar .NET Framework origem | Microsoft Docs'
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
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205441"
---
# <a name="how-to-debug-net-framework-source"></a>Como depurar a origem do .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece novos recursos para [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] depuração. Para depurar a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origem, você deve ter acesso à depuração de símbolos para o código. Você também precisa habilitar a depuração na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origem.  
  
 Você pode habilitar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] o download de revisões e símbolos na caixa de diálogo **Opções** . Ao habilitar a transferência de símbolo, você pode optar por baixar imediatamente os símbolos ou apenas habilitar a opção para uma transferência posterior. Se você não baixar os símbolos imediatamente, eles serão baixados da próxima vez em que você iniciar a depuração do seu aplicativo. Você também pode fazer um download manual na janela **módulos** ou na janela **pilha de chamadas** .  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para ativar a depuração de origem do .NET Framework  
  
1. No menu **Ferramentas** , clique em **Opções**.  
  
2. Na caixa de diálogo **Opções** , clique na categoria **depuração** .  
  
3. Na caixa **geral** , defina **habilitar .NET Framework** a depuração de origem.  
  
    1. Se Apenas Meu Código tiver sido habilitado, uma caixa de diálogo de aviso mostrará que Apenas Meu Código está desabilitado agora. Clique em **OK**.  
  
    2. Se você não tiver um local de cache de símbolo definido, outra caixa de diálogo de aviso informará que um local padrão de cache do símbolo foi definido agora. Clique em **OK**.  
  
4. Na categoria **depuração** , clique em **símbolos**.  
  
5. Se você desejar alterar o local do cache de símbolos:  
  
    1. Abra o nó de **depuração** na caixa à esquerda.  
  
    2. No nó **depuração** , clique em **símbolos**.  
  
    3. Edite o local em **símbolos de cache dos servidores de símbolo para esse diretório** ou clique em **procurar** para escolher um local.  
  
6. Se você quiser baixar símbolos imediatamente, clique em **carregar símbolos usando os locais acima**.  
  
     Este botão não está disponível no modo de design.  
  
     Se você não optar por baixar símbolos agora, os símbolos serão baixados automaticamente da próxima vez em que você iniciar a depuração do seu programa.  
  
7. Clique em **OK** para fechar a caixa de diálogo **Opções** .  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para carregar símbolos de Framework usando a janela de módulos  
  
1. Na janela **módulos** , clique com o botão direito do mouse em um módulo para o qual os símbolos não são carregados. Você pode saber se os símbolos são carregados ou não examinando a coluna **status de símbolos** .  
  
2. Aponte para **carregar símbolos do** e clique em **servidores de símbolos da Microsoft** para baixar símbolos do servidor de símbolos públicos da Microsoft ou caminho de **símbolo** para carregar de um diretório em que você armazenou anteriormente os símbolos.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para carregar símbolos de Framework usando a janela de pilha de chamadas  
  
1. Na janela **pilha de chamadas** , clique com o botão direito do mouse em um quadro para o qual os símbolos não são carregados. O quadro será esmaecido.  
  
2. Aponte para **carregar símbolos de** e clique em **servidores de símbolos da Microsoft** ou caminho de **símbolo**.  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração de código gerenciado](../debugger/debugging-managed-code.md)   
 [Especificar os arquivos de origem e símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
