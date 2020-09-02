---
title: Depuração de aplicativos ClickOnce que usam System. Deployment. Application | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0b12faf451d3ed9bb70e2bb1ec6c8503cfb86d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187791"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Depurando aplicativos ClickOnce que usam System.Deployment.Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a implantação permite que você configure como um aplicativo é atualizado. No entanto, se você precisar usar e personalizar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] recursos de implantação avançados, será necessário acessar o modelo de objeto de implantação fornecido pelo <xref:System.Deployment.Application> . Você pode usar as <xref:System.Deployment.Application> APIs para tarefas avançadas, como:  
  
- Criando uma opção "atualizar agora" em seu aplicativo  
  
- Downloads condicionais e sob demanda de vários componentes de aplicativos  
  
- Atualizações integradas diretamente ao aplicativo  
  
- Garantindo que o aplicativo cliente esteja sempre atualizado  
  
  Como as <xref:System.Deployment.Application> APIs só funcionam quando um aplicativo é implantado com [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnologia, a única maneira de depurá-las é implantar o aplicativo usando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , anexá-lo e depurá-lo. Pode ser difícil anexar o depurador cedo o suficiente, pois esse código geralmente é executado quando o aplicativo é iniciado e executado antes que você possa anexar o depurador. Uma solução é fazer interrupções (ou interrupções, para projetos Visual Basic) antes do código de verificação de atualização ou código sob demanda.  
  
  A técnica de depuração recomendada é a seguinte:  
  
1. Antes de começar, verifique se o símbolo (. pdb) e os arquivos de origem estão arquivados.  
  
2. Implante a versão 1 do aplicativo.  
  
3. Crie uma nova solução em branco. No menu **Arquivo**, clique em **Novo** e, em seguida em **Projeto**. Na caixa de diálogo **novo projeto** , abra o nó **outros tipos de projeto** e, em seguida, selecione a pasta **soluções do Visual Studio** . No painel **modelos** , selecione **solução em branco**.  
  
4. Adicione o local de origem arquivado às propriedades dessa nova solução. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó da solução e clique em **Propriedades**. Na caixa de diálogo **páginas de propriedades** , selecione **depurar arquivos de origem**e, em seguida, adicione o diretório do código-fonte arquivado. Caso contrário, o depurador encontrará os arquivos de origem desatualizados, já que os caminhos do arquivo de origem são registrados no arquivo. pdb. Se o depurador usar arquivos de origem desatualizados, você verá uma mensagem informando que a origem não corresponde.  
  
5. Verifique se o depurador pode encontrar os arquivos. pdb. Se você os tiver implantado com seu aplicativo, o depurador os encontrará automaticamente. Ele sempre aparece ao lado do assembly em questão primeiro. Caso contrário, será necessário adicionar o caminho de arquivo morto para os **locais de arquivos de símbolo (. pdb)** (para acessar essa opção, no menu **ferramentas** , clique em **Opções**, abra o nó **depuração** e clique em **símbolos**).  
  
6. Depurar o que acontece entre `CheckForUpdate` as `Download` / `Update` chamadas de método e.  
  
    Por exemplo, o código de atualização pode ser o seguinte:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Implante a versão 2.  
  
8. Tentativa de anexar o depurador ao aplicativo da versão 1, pois ele baixa uma atualização para a versão 2. Como alternativa, você pode usar o `System.Diagnostics.Debugger.Break` método ou simplesmente `Stop` em Visual Basic. É claro que você não deve deixar essas chamadas de método no código de produção.  
  
    Por exemplo, suponha que você esteja desenvolvendo um aplicativo Windows Forms e tenha um manipulador de eventos para esse método com a lógica de atualização nele. Para depurar isso, basta anexar antes de o botão ser pressionado e, em seguida, definir um ponto de interrupção (certifique-se de abrir o arquivo arquivado apropriado e definir o ponto de interrupção nele).  
  
   Use a <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propriedade para invocar as <xref:System.Deployment.Application> APIs somente quando o aplicativo for implantado; as APIs não devem ser invocadas durante a depuração no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Consulte Também  
 <xref:System.Deployment.Application>
