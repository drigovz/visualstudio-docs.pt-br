---
title: Perguntas frequentes sobre depuração de instantâneo | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43b76ad81a2c075a11ff55dcbd7fbc5e8a4b3fe7
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431847"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Perguntas frequentes sobre depuração de instantâneo no Visual Studio

Veja a seguir uma lista de perguntas que podem surgir durante a depuração de aplicativos dinâmicos do Azure usando o Depurador de Instantâneos.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qual é o custo de desempenho de capturar um instantâneo?

Quando o Depurador de Instantâneos captura um instantâneo do seu aplicativo, ele bifurca o processo do aplicativo e suspende a cópia bifurcada. Ao depurar um instantâneo, você o está depurando em relação à cópia bifurcada do processo. Esse processo leva apenas 10 a 20 milissegundos, mas não copia o heap completo do aplicativo. Em vez disso, copia apenas a tabela de página e define as páginas para cópia na gravação. Se algum dos objetos do seu aplicativo no heap for alterado, as respectivas páginas serão copiadas. Isso porque cada instantâneo tem um pequeno custo na memória (na ordem de centenas de kilobytes para a maioria dos aplicativos).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>O que acontece se eu tiver um Serviço de Aplicativo do Azure expandido (várias instâncias do meu aplicativo)?

Quando você tiver várias instâncias do seu aplicativo, os snappoints serão aplicados a cada instância única. Somente o primeiro snappoint a atender às condições especificadas cria um instantâneo. Se você tiver vários snappoints, instantâneos posteriores serão provenientes da mesma instância que criou o primeiro instantâneo. Logpoints enviados para a janela de saída mostrarão apenas as mensagens de uma instância, enquanto logpoints enviados para os logs de aplicativo enviarão mensagens de todas as instâncias.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Como o Depurador de Instantâneos carrega símbolos?

O Depurador de Instantâneos requer que você tenha os símbolos correspondentes para seu aplicativo no local ou implantados no Serviço de Aplicativo do Azure. (No momento, não há suporte para PDBs inseridos). O Depurador de Instantâneos baixa automaticamente os símbolos de seu Serviço de Aplicativo do Azure. A partir do Visual Studio 2017 versão 15.2, a implantação no Serviço de Aplicativo do Azure também faz a implantação dos símbolos do seu aplicativo.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>O Depurador de Instantâneos funciona em builds de versão do meu aplicativo?

Sim, o Depurador de Instantâneos deve funcionar em builds de versão. Quando um snappoint for colocado em uma função, a função será recompilada para uma versão de depuração, tornando-o depurável. A interrupção do Depurador de Instantâneos retorna funções para a versão do build de versão.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Os logpoints pode causar efeitos colaterais no meu aplicativo de produção?

Não. As mensagens de log que você adiciona ao seu aplicativo são avaliadas virtualmente. Elas não podem causar efeitos colaterais em seu aplicativo. No entanto, algumas propriedades nativas podem não ser acessíveis com logpoints.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>O Depurador de Instantâneos funcionará se meu servidor estiver sob carga?

Sim, a depuração de instantâneos pode funcionar em servidores sob carga. O Depurador de Instantâneos faz a restrição e não captura instantâneos em situações em que há uma quantidade pequena de memória livre em seu servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Como faço para desinstalar o Depurador de Instantâneos?

Você pode desinstalar a extensão de site do Depurador de Instantâneos no seu Serviço de Aplicativo com as seguintes etapas:

1. Desative o serviço de aplicativo por meio do Gerenciador de nuvem no Visual Studio ou o portal do Azure.
1. Navegue até o site do Kudu do Serviço de Aplicativo (ou seja, seu serviçodeaplicativo.**scm**.azurewebsites.net) e vá até **Extensões de Site**.
1. Clique no X na extensão de site do Depurador de Instantâneos para removê-lo.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Por que as portas ficam abertas durante uma sessão do Depurador de Instantâneos?

O Depurador de Instantâneos precisa abrir um conjunto de portas para depurar os instantâneos tirados no Azure. São as mesmas portas necessárias para depuração remota. [Encontre a lista de portas aqui](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Como desabilitar a extensão de depurador remoto?

Para serviços de aplicativo:
1. Desabilite a extensão de depurador remoto por meio do portal do Azure para seu serviço de aplicativo.
2. Portal do Azure > sua folha de recursos do serviço de aplicativo > *as configurações do aplicativo*
3. Navegue até a *depuração* seção e clique no *Off* botão *depuração remota*.

Para o AKS:
1. Atualizar o Dockerfile para remover as seções correspondentes para o [Visual Studio Snapshot Debugger em imagens do Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile e reimplante a imagem do Docker modificada.

Para o dimensionamento de máquinas virtuais de máquina virtual/conjuntos de remover os pools de NAT de entrada e de KeyVaults de extensão, certificados, do depurador remoto da seguinte maneira:

1. Remover extensão de depurador remoto  

   Há várias maneiras para desabilitar o depurador remoto para máquinas virtuais e conjuntos de dimensionamento de máquina virtual:  

      - Desabilitar o depurador remoto por meio do Gerenciador de nuvem  

         - Cloud Explorer > seu recurso de máquina virtual > Desabilitar depuração (desabilitar a depuração não existe para definir no Cloud Explorer de dimensionamento de máquinas virtuais).  


      - Desabilitar o depurador remoto com Scripts/Cmdlets do PowerShell  

         Para a máquina virtual:  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Para conjuntos de dimensionamento de máquina virtual:  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Desabilitar o depurador remoto por meio do portal do Azure
         - Portal do Azure > seu dimensionamento de máquinas virtuais/máquina virtual define folha de recursos > extensões  
         - Desinstalar a extensão Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  


         > [!NOTE]
         > Conjuntos de dimensionamento de máquina virtual - o portal não permite remover as portas DebuggerListener. Você precisará usar o Azure PowerShell. Veja mais detalhes a seguir.
  
2. Remover certificados e o Cofre de chaves do Azure

   Ao instalar a extensão de depurador remoto para máquinas virtuais ou conjuntos de dimensionamento de máquina virtual, os certificados de cliente e servidor são criados para autenticar o cliente do VS com a máquina Virtual do Azure/recursos de conjuntos de dimensionamento de máquina virtual.  

   - O certificado do cliente  

      Esse certificado é um certificado autoassinado, localizado em Cert: / CurrentUser/My /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      Uma maneira de remover este certificado de sua máquina é por meio do PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - O certificado do servidor
      - A impressão digital certificado de servidor correspondente é implantada como um segredo do Cofre de chaves do Azure. VS tentará localizar ou criar um cofre de chaves com o prefixo MSVSAZ * na região correspondente à máquina virtual ou o recurso de conjuntos de dimensionamento de máquina virtual. Conjuntos de dimensionamento de máquina virtual ou máquina virtual de todos os recursos implantados para essa região, portanto, compartilharão o mesmo Cofre de chaves.  
      - Para excluir o segredo de impressão digital do certificado de servidor, acesse o portal do Azure e encontre o KeyVault MSVSAZ * na mesma região que está hospedando o seu recurso. Excluir o segredo que deve ser rotulado `remotedebugcert<<ResourceName>>`  
      - Você também precisará excluir o segredo do servidor do seu recurso por meio do PowerShell.  

      Para máquinas virtuais:  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Para conjuntos de dimensionamento de máquina virtual:  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Remova todos os pools de NAT de entrada DebuggerListener (escala de máquina virtual definido apenas)  

   O depurador remoto apresenta DebuggerListener pools de NAT de entrada que são aplicados ao balanceador de carga do seu conjunto de dimensionamento.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Como desabilitar o depurador de instantâneo?

Para o serviço de aplicativo:
1. Desabilite o depurador de instantâneo por meio do portal do Azure para seu serviço de aplicativo.
2. Portal do Azure > sua folha de recursos do serviço de aplicativo > *as configurações do aplicativo*
3. Exclua as seguintes configurações de aplicativo no portal do Azure e salvar suas alterações. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Qualquer alteração nas configurações do aplicativo iniciará uma reinicialização do aplicativo. Detalhes sobre as configurações do aplicativo podem ser encontrados [aqui](https://docs.microsoft.com/azure/app-service/web-sites-configure#app-settings). 

Para o AKS:
1. Atualizar o Dockerfile para remover as seções correspondentes para o [Visual Studio Snapshot Debugger em imagens do Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile e reimplante a imagem do Docker modificada.

Para conjuntos de dimensionamento de máquina virtual/máquina virtual:

Há várias maneiras para desabilitar o depurador de instantâneo:
- Cloud Explorer > recurso de conjunto de dimensionamento de máquina virtual/máquina virtual > desabilitar o diagnóstico

- Portal do Azure > folha de recursos de conjunto de dimensionamento de máquina virtual/máquina virtual > extensões > desinstalar vmdiagnosticssettings extensão

- Cmdlets do PowerShell da [Az PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Máquina virtual:
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    Conjuntos de dimensionamento de máquina virtual:
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.md)
- [Depurar aplicativos ASP.NET dinâmicos usando o depurador de instantâneo](../debugger/debug-live-azure-applications.md)
- [Conjuntos de dimensionamento de máquinas virtuais de Machines\Virtual do ASP.NET do Azure ao vivo usando o depurador de instantâneo de depuração](../debugger/debug-live-azure-virtual-machines.md)
- [Depurar ao vivo ASP.NET Azure Kubernetes usando o depurador de instantâneo](../debugger/debug-live-azure-kubernetes.md)
- [Solução de problemas e problemas conhecidos para depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md)