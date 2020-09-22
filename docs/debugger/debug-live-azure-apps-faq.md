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
ms.openlocfilehash: f8afc67b92a943dd571847bb1a00fb7e4db4514b
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851093"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Perguntas frequentes sobre depuração de instantâneo no Visual Studio

Veja a seguir uma lista de perguntas que podem surgir durante a depuração de aplicativos dinâmicos do Azure usando o Depurador de Instantâneos.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qual é o custo de desempenho de capturar um instantâneo?

Quando o Depurador de Instantâneos captura um instantâneo do seu aplicativo, ele bifurca o processo do aplicativo e suspende a cópia bifurcada. Ao depurar um instantâneo, você o está depurando em relação à cópia bifurcada do processo. Esse processo leva apenas 10 a 20 milissegundos, mas não copia o heap completo do aplicativo. Em vez disso, copia apenas a tabela de página e define as páginas para cópia na gravação. Se algum dos objetos do seu aplicativo no heap for alterado, as respectivas páginas serão copiadas. Isso porque cada instantâneo tem um pequeno custo na memória (na ordem de centenas de kilobytes para a maioria dos aplicativos).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>O que acontece se eu tiver um Serviço de Aplicativo do Azure expandido (várias instâncias do meu aplicativo)?

Quando você tiver várias instâncias do seu aplicativo, os snappoints serão aplicados a cada instância única. Somente o primeiro snappoint a atender às condições especificadas cria um instantâneo. Se você tiver vários snappoints, instantâneos posteriores serão provenientes da mesma instância que criou o primeiro instantâneo. Logpoints enviados para a janela de saída mostrarão apenas as mensagens de uma instância, enquanto logpoints enviados para os logs de aplicativo enviarão mensagens de todas as instâncias.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Como o Depurador de Instantâneos carrega símbolos?

O Depurador de Instantâneos requer que você tenha os símbolos correspondentes para seu aplicativo no local ou implantados no Serviço de Aplicativo do Azure. (Não há suporte para PDBs inseridos no momento.) O Depurador de Instantâneos baixa automaticamente os símbolos do seu serviço de Azure App. A partir do Visual Studio 2017 versão 15.2, a implantação no Serviço de Aplicativo do Azure também faz a implantação dos símbolos do seu aplicativo.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>O Depurador de Instantâneos funciona em builds de versão do meu aplicativo?

Sim, o Depurador de Instantâneos deve funcionar em builds de versão. Quando um snappoint for colocado em uma função, a função será recompilada para uma versão de depuração, tornando-o depurável. A interrupção do Depurador de Instantâneos retorna funções para a versão do build de versão.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Os logpoints pode causar efeitos colaterais no meu aplicativo de produção?

Não. As mensagens de log que você adiciona ao seu aplicativo são avaliadas virtualmente. Elas não podem causar efeitos colaterais em seu aplicativo. No entanto, algumas propriedades nativas podem não ser acessíveis com logpoints.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>O Depurador de Instantâneos funcionará se meu servidor estiver sob carga?

Sim, a depuração de instantâneos pode funcionar em servidores sob carga. O Depurador de Instantâneos faz a restrição e não captura instantâneos em situações em que há uma quantidade pequena de memória livre em seu servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Como faço para desinstalar o Depurador de Instantâneos?

Você pode desinstalar a extensão de site do Depurador de Instantâneos no seu Serviço de Aplicativo com as seguintes etapas:

1. Desative o serviço de aplicativo por meio do Cloud Explorer no Visual Studio ou no portal do Azure.
1. Navegue até o site do Kudu do Serviço de Aplicativo (ou seja, seu serviçodeaplicativo.**scm**.azurewebsites.net) e vá até **Extensões de Site**.
1. Clique no X na extensão de site do Depurador de Instantâneos para removê-lo.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Por que as portas ficam abertas durante uma sessão do Depurador de Instantâneos?

O Depurador de Instantâneos precisa abrir um conjunto de portas para depurar os instantâneos tirados no Azure. São as mesmas portas necessárias para depuração remota. [Encontre a lista de portas aqui](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Como fazer desabilitar a extensão do depurador remoto?

Para serviços de aplicativos:
1. Desabilite a extensão do depurador remoto por meio do portal do Azure para seu serviço de aplicativo.
2. Portal do Azure > folha de recursos do serviço de aplicativo > *configurações do aplicativo*
3. Navegue até a seção *depuração* e clique no botão *desligar* para a *depuração remota*.

Para AKS:
1. Atualize seu Dockerfile para remover as seções correspondentes à [depurador de instantâneos do Visual Studio em imagens do Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile e reimplante a imagem do Docker modificada.

Para os conjuntos de dimensionamento de máquinas virtuais/máquina virtual, remova a extensão do depurador remoto, os certificados, os compartimentos de chaves e os pools de NAT de entrada da seguinte maneira:

1. Remover extensão do depurador remoto

   Há várias maneiras de desabilitar o depurador remoto para máquinas virtuais e conjuntos de dimensionamento de máquinas virtuais:

      - Desabilitar o depurador remoto por meio do Cloud Explorer

         - O Cloud Explorer > seu recurso de máquina virtual > desabilitar a depuração (desabilitar a depuração não existe para o conjunto de dimensionamento de máquinas virtuais no Cloud Explorer).

      - Desabilitar o depurador remoto com os scripts/cmdlets do PowerShell

         Para a máquina virtual:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Para conjuntos de dimensionamento de máquinas virtuais:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Desabilite o depurador remoto por meio do portal do Azure
         - Portal do Azure > suas extensões de máquina virtual/conjunto de dimensionamento de máquinas virtuais > Extensions
         - Desinstalar a extensão Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Conjuntos de dimensionamento de máquinas virtuais-o portal não permite remover as portas DebuggerListener. Você precisará usar Azure PowerShell. Confira os detalhes abaixo.

2. Remover certificados e o cofre de chaves do Azure

   Ao instalar a extensão do depurador remoto para a máquina virtual ou conjuntos de dimensionamento de máquinas virtuais, os certificados de cliente e de servidor são criados para autenticar o cliente do Visual Studio com os recursos de máquina virtual/conjuntos de dimensionamento de máquinas virtuais do Azure.

   - O certificado do cliente

      Esse CERT é um certificado autoassinado localizado em CERT:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Uma maneira de remover esse certificado do seu computador é por meio do PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - O certificado do servidor
      - A impressão digital do certificado de servidor correspondente é implantada como um segredo para o Azure keyvault. O Visual Studio tentará localizar ou criar um keyvault com o prefixo MSVSAZ * na região correspondente à máquina virtual ou ao recurso de conjuntos de dimensionamento de máquinas virtuais. Todos os recursos de máquina virtual ou de conjuntos de dimensionamento de máquinas virtuais implantados nessa região compartilharão o mesmo keyvault.
      - Para excluir o segredo de impressão digital do certificado do servidor, acesse o portal do Azure e localize o MSVSAZ * keyvault na mesma região que está hospedando seu recurso. Excluir o segredo que deve ser rotulado `remotedebugcert<<ResourceName>>`
      - Você também precisará excluir o segredo do servidor do seu recurso por meio do PowerShell.

      Para máquinas virtuais:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Para conjuntos de dimensionamento de máquinas virtuais:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Remover todos os pools de NAT de entrada do DebuggerListener (somente conjunto de dimensionamento de máquinas virtuais)

   O depurador remoto introduz DebuggerListener pools NAT vinculados que são aplicados ao balanceador de carga do scaleset.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Como fazer desabilitar Depurador de Instantâneos?

Para o serviço de aplicativo:
1. Desabilite Depurador de Instantâneos por meio do portal do Azure para seu serviço de aplicativo.
2. Portal do Azure > folha de recursos do serviço de aplicativo > *configurações do aplicativo*
3. Exclua as configurações de aplicativo a seguir no portal do Azure e salve as alterações.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > As alterações nas configurações do aplicativo iniciarão uma reinicialização do aplicativo. Para obter mais informações sobre as configurações do aplicativo, consulte [configurar um aplicativo do serviço de aplicativo no portal do Azure](/azure/app-service/web-sites-configure).

Para AKS:
1. Atualize seu Dockerfile para remover as seções correspondentes à [depurador de instantâneos do Visual Studio em imagens do Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile e reimplante a imagem do Docker modificada.

Para conjuntos de dimensionamento de máquinas virtuais/máquina virtual:

Há várias maneiras de desabilitar o Depurador de Instantâneos:
- Cloud Explorer > seu recurso de máquina virtual/conjunto de dimensionamento de máquinas virtuais > desabilitar o diagnóstico

- Portal do Azure > a folha de recursos da máquina virtual/conjunto de dimensionamento de máquinas virtuais > extensões > desinstalar a extensão Microsoft. insights. VMDiagnosticsSettings

- Cmdlets do PowerShell do [AZ PowerShell](/powershell/azure/overview)

   Máquina virtual:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Conjuntos de dimensionamento de máquinas virtuais:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Confira também

- [Depurando no Visual Studio](../debugger/index.yml)
- [Depurar aplicativos ASP.NET dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-applications.md)
- [Depurar conjuntos de dimensionamento de máquinas Machines\Virtual virtuais do ASP.NET do Azure em tempo real usando o Depurador de Instantâneos](../debugger/debug-live-azure-virtual-machines.md)
- [Depurar Kubernetes ASP.NET dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-kubernetes.md)
- [Solução de problemas e problemas conhecidos da depuração de instantâneos](../debugger/debug-live-azure-apps-troubleshooting.md)
