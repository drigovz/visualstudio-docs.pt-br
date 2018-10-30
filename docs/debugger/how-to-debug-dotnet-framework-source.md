---
title: 'Como: depurar o código-fonte do .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c06a2328987201198bc2d5d15a4788d2a821d7b6
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219114"
---
# <a name="how-to-debug-net-framework-source"></a>Como depurar a origem do .NET Framework
Para depurar o código-fonte do .NET Framework, você deve ter acesso aos símbolos de depuração para o código. Você também precisará habilitar a depuração de código-fonte do .NET Framework.  
  
 Você pode habilitar o .NET Framework passo a passo e o download do símbolo na **opções** caixa de diálogo. Ao habilitar a transferência de símbolo, você pode optar por baixar imediatamente os símbolos ou apenas habilitar a opção para uma transferência posterior. Se você não baixar os símbolos imediatamente, eles serão baixados da próxima vez em que você iniciar a depuração do seu aplicativo. Você também pode baixar um manual do **módulos** janela ou o **pilha de chamadas** janela.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para ativar a depuração de origem do .NET Framework  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  No **opções** caixa de diálogo, clique o **depuração** categoria.  
  
3.  No **gerais** , defina **origem de habilitar o .NET Framework passo a passo.**  
  
    1.  Se Apenas Meu Código tiver sido habilitado, uma caixa de diálogo de aviso mostrará que Apenas Meu Código está desabilitado agora. Clique em **OK**.  
  
    2.  Se você não tiver um local de cache de símbolo definido, outra caixa de diálogo de aviso informará que um local padrão de cache do símbolo foi definido agora. Clique em **OK**.  
  
4.  Sob o **Debugging** categoria, clique em **símbolos**.  
  
5.  Se você quiser alterar o local do cache de símbolos, edite o local em **armazenar em Cache os símbolos neste diretório** ou clique em **procurar** para escolher um local.  
  
6.  Se você quiser baixar símbolos imediatamente, clique em **carregar símbolos usando os locais acima**.  
  
     Esse botão não está disponível no modo de design, mas está disponível durante a depuração.  
  
     Se você não optar por baixar símbolos agora, os símbolos serão baixados automaticamente da próxima vez em que você iniciar a depuração do seu programa.  
  
7.  Clique em **OK** para fechar a caixa de diálogo **Opções**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para carregar símbolos de Framework usando a janela de módulos  
  
1.  No **módulos** janela (durante a depuração, escolha **Debug** > **Windows** > **módulos**), Clique com botão direito um módulo para o qual os símbolos não foram carregados. Você pode informar se os símbolos são carregados ou não examinando os **Status de símbolos** coluna.  
  
2.  Aponte para **configurações de símbolo** e clique em **servidores de símbolo Microsoft** para baixar os símbolos do servidor de símbolos públicos de Microsoft. Ou, o módulo com o botão direito e escolha **carregar símbolos** para carregar a partir de um diretório onde você armazenou símbolos anteriormente.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para carregar símbolos de Framework usando a janela de pilha de chamadas  
  
1.  No **pilha de chamadas** janela, o botão direito do mouse um quadro para o qual os símbolos não foram carregados. O quadro será esmaecido.  
  
2.  Aponte para **configurações de símbolo** e clique em **servidores de símbolo Microsoft**, ou o módulo com o botão direito e escolha **caminho de símbolo**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)