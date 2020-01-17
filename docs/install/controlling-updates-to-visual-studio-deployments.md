---
title: Controlar atualizações em implantações
description: Saiba como alterar o local onde o Visual Studio busca atualizações quando você instala usando uma rede.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8743f042c7c33da34895f93e5df3990f6e0b2ed2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115315"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Atualizações de controle para implantações do Visual Studio com base em rede

Geralmente, os administradores corporativos criam um layout e o hospedam em um compartilhamento de arquivo de rede para implantação para seus usuários finais.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Controlar onde o Visual Studio procura atualizações

Por padrão, o Visual Studio continuará a procurar atualizações online, mesmo se a instalação for implantada de um compartilhamento de rede. Se uma atualização estiver disponível, o usuário poderá instalá-la. Qualquer conteúdo atualizado não encontrado no layout offline é baixado da Web.

Se você quiser controle direto sobre onde o Visual Studio procura por atualizações, modifique o local em que ele procura. Você também pode controlar a versão para a qual os usuários fazem atualização. Para fazer isso, siga estas etapas:

1. Crie um layout offline:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Copie-o para o compartilhamento de arquivo onde você deseja hospedá-lo:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Modifique o arquivo response.json no layout e altere o valor `channelUri` para apontar para uma cópia de channelManifest.json que o administrador controla.

   Verifique se você escapou barras invertidas no valor, assim como no exemplo a seguir:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Agora os usuários finais podem executar a instalação deste compartilhamento para instalar o Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Quando um administrador corporativo determina que é hora de os usuários atualizarem para uma versão mais recente do Visual Studio, eles podem [atualizar a localização do layout](update-a-network-installation-of-visual-studio.md) para incorporar os arquivos atualizados, conforme demonstrado a seguir.

1. Use um comando semelhante ao comando a seguir:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Verifique se o arquivo response.json no layout atualizado ainda contém as personalizações, especificamente a modificação de channelUri, conforme demonstrado a seguir:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Instalações existentes do Visual Studio desse layout procuram atualizações em `\\server\share\VS\ChannelManifest.json`. Se o channelManifest.json for mais recente do que o já instalado pelo usuário, o Visual Studio notificará o usuário de que uma atualização está disponível.

   Novas instalações instalam automaticamente a versão atualizada do Visual Studio diretamente do layout.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Notificações de controle no IDE do Visual Studio

::: moniker range="vs-2017"

Conforme descrito anteriormente, o Visual Studio verifica o local do qual foi instalado, tal como um compartilhamento de rede ou a Internet, para ver se há atualizações disponíveis. Quando uma atualização está disponível, o Visual Studio notifica o usuário com um sinalizador de notificação no canto superior direito da janela.

   ![Sinalizador de notificação de atualizações](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Conforme descrito anteriormente, o Visual Studio verifica o local do qual foi instalado, tal como um compartilhamento de rede ou a Internet, para ver se há atualizações disponíveis. Quando uma atualização está disponível, o Visual Studio notifica o usuário com um ícone de notificação no canto inferior direito da janela.

   ![O ícone de notificação no IDE do Visual Studio](media/vs-2019/notification-bar.png "O ícone de notificação no IDE do Visual Studio")

::: moniker-end

Se não quiser que os usuários finais sejam notificados sobre atualizações, desabilite as notificações. (Por exemplo, você talvez queira desabilitar as notificações se fornecer atualizações por meio de um mecanismo de distribuição de software central.)

::: moniker range="vs-2017"

Já que o Visual Studio 2017 [Armazena as entradas do Registro em um Registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), você não pode editar diretamente o Registro da maneira típica. No entanto, o Visual Studio inclui um utilitário `vsregedit.exe` que você pode usar para alterar as configurações do Visual Studio. Você pode desativar as notificações com o seguinte comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Já que o Visual Studio 2019 [armazena as entradas do Registro em um Registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), você não pode editar diretamente o Registro da maneira típica. No entanto, o Visual Studio inclui um utilitário `vsregedit.exe` que você pode usar para alterar as configurações do Visual Studio. Você pode desativar as notificações com o seguinte comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Verifique se você substituiu o diretório para coincidir com a instância instalada que você deseja editar.)

> [!TIP]
> Use [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) para localizar uma instância específica do Visual Studio em uma estação de trabalho cliente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Veja também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Ferramentas para gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Ciclo de vida e manutenção do produto Visual Studio](/visualstudio/releases/2019/servicing/)
