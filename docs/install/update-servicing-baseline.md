---
title: Atualizar o Visual Studio enquanto estiver em uma linha de base de manutenção
titleSuffix: ''
description: Aprenda como atualizar o Visual Studio enquanto estiver em uma linha de base de manutenção.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8928feffed77f8bfbb3787bd9a20737b9c7b3f9e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66213777"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Atualizar o Visual Studio enquanto estiver em uma linha de base de manutenção

O Visual Studio de 2019 terá atualizações frequentes durante seu [ciclo de vida do produto](/visualstudio/productinfo/release-rhythm.md#release-channel-updates). Isso incluirá as atualizações de versão secundária (por exemplo: 16.0 até 16.1) que podem incluir novos recursos e componentes e atualizações de manutenção (por exemplo: 16.0.4 até 16.0.5) que contêm correções destinadas apenas para problemas críticos. 

Os administradores de empresa podem optar por manter seus clientes em uma linha de base de manutenção, que tem suporte das atualizações de manutenção por um ano após o lançamento da próxima linha de base de manutenção. Isso permite mais flexibilidade para desenvolvedores e administradores na adoção de novos recursos, correções de bug ou componentes incluídos nas novas atualizações secundárias. A primeira linha de base de manutenção é a 16.0.x. Confira [Opções de suporte para clientes empresariais e profissionais](/visualstudio/releases/2019/servicing.md#support-options-for-enterprise-and-professional-customers) para saber mais.

## <a name="how-to-get-onto-a-servicing-baseline"></a>Como obter uma linha de base de manutenção

Para começar a usar uma linha de base de manutenção, baixe um inicializador do instalador da versão corrigida do Visual Studio em [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Esses inicializadores têm links para as configurações do produto, as cargas de trabalho e componentes dessa versão específica. 

> [!NOTE]
> Tenha cuidado ao distinguir entre os inicializadores de versão corrigida e normal. Os inicializadores normais são configurados para usar a versão mais recente disponível do Visual Studio. Eles têm um número no nome do arquivo (por exemplo: vs_enterprise__123456789-123456789.exe) ao serem baixadas de my.visualstudio.com.

Durante a instalação, os administradores de empresa precisam configurar seus clientes para impedir que eles atualizem para a versão mais recente. Isso pode ser feito [alterando a configuração channelUri no arquivo de configuração de resposta](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) para usar um manifesto do canal na pasta local ou no layout ao [modificar o channelUri por meio da execução de linha de comando](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) para usar um arquivo inexistente ou ao [definir políticas no sistema cliente para desabilitar atualizações](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating) para impedir a atualização automática dos clientes. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalar uma linha de base de manutenção em uma rede

Para administradores que usam uma instalação de layout de rede, modifique o valor de channelUri na `response.json` no layout para usar o channelmanifest.json que está na mesma pasta. Confira [Controlar atualizações para implantações do Visual Studio baseadas em rede](controlling-updates-to-visual-studio-deployments.md) para obter um guia passo a passo. Alterar o channelUri permite que os clientes procurem atualizações no local de layout. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalar uma linha de base de manutenção via internet

Se for uma instalação baseada na internet, adicione `--channelUri` com um manifesto de canal inexistente à linha de comando usada para iniciar a instalação. Isso desabilita o Visual Studio de usar a versão mais recente disponível para uma atualização. Veja um exemplo:

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Use as configurações de política para desabilitar clientes da atualização

Outra opção para controlar as atualizações em um cliente é [desativar as notificações de atualização](controlling-updates-to-visual-studio-deployments.md). Use esta opção se o valor de channelUri não foi alterado na instalação. Ele impedirá que o cliente receba links da última versão disponível. Um inicializador de versão fixa ainda é necessário para atualizar para uma versão específica no cliente.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Como manter-se em uma linha de base de manutenção

Quando há uma atualização para uma linha de base de manutenção, os arquivos do inicializador de versão fixa são disponibilizados para a atualização da manutenção do [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Eles podem ser usados em vários cenários.

Para os administradores implantando via instalação de layout de rede, o administrador desejará atualizar a [localização do layout](update-a-network-installation-of-visual-studio.md). Os clientes que instalaram do local receberão as notificações de atualização. Se precisar implantar a atualização nos clientes, siga [estas instruções](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Ao modificar o 'response.json' para uma atualização, não adicione cargas de trabalho, componentes ou idiomas adicionais. O gerenciamento dessas configurações deve ser feito como uma implantação 'modificar', depois que o produto foi atualizado. 

Se for uma instalação baseada na internet, execute o novo instalador de versão fixa com o parâmetro `--channelUri` apontando para um manifesto de canal inexistente no cliente. Se a atualização for implantada no modo silencioso ou passivo, use dois comandos separados:

1. Primeiro, atualize o Instalador do Visual Studio: <br>```vs_enterprise.exe --quiet --update```
2. Depois, atualize o aplicativo do Visual Studio em si: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Como definir as configurações em um arquivo de resposta](automated-installation-with-response-file.md)
* [Atualizações de controle para implantações do Visual Studio com base em rede](controlling-updates-to-visual-studio-deployments.md)
* [Ciclo de vida e manutenção do produto Visual Studio](/visualstudio/releases/2019/servicing/)
