---
title: Depurar aplicativos .NET Core no WSL 2
description: Aprenda a executar e depurar seus aplicativos do .NET Core no WSL 2 sem sair do Visual Studio.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 736987a02ca7e2f59ce689b8402d9a6fcd7407e9
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99227641"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Depurar aplicativos .NET Core no WSL 2 com o Visual Studio

Você pode executar e depurar facilmente seus aplicativos .NET Core no Linux sem sair do Visual Studio usando o WSL 2. Se você for um desenvolvedor de plataforma cruzada, poderá usar esse método como uma maneira simples de testar mais de seus ambientes de destino.

Para um usuário do Windows .NET destinado ao Linux, o WSL 2 mora em um ponto forte entre o realm de produção e a produtividade. No Visual Studio, você já pode depurar em um ambiente Linux remoto usando o [depurador remoto](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)ou com contêineres usando as [ferramentas de contêiner](../containers/overview.md). Quando o realm de produção é sua preocupação principal, você deve usar uma dessas opções. Quando um loop interno fácil e rápido é mais importante, WSL 2 é uma ótima opção.

Você não precisa escolher apenas um método! Você pode ter um perfil de inicialização para Docker e WSL 2 no mesmo projeto e escolher o que for apropriado para uma execução específica. E, depois que seu aplicativo for implantado, você sempre poderá usar o depurador remoto para se conectar a ele se houver um problema.

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2019 v 16.9 Preview 1 ou versões posteriores com a depuração do .NET Core com o componente opcional WSL 2.

  O componente opcional é incluído por padrão com as cargas de trabalho de plataforma cruzada do .NET Core ou ASP.NET e desenvolvimento para a Web. Você deve instalar uma ou ambas as cargas de trabalho.

- Instale o [WSL 2](/windows/wsl/about).

- Instale a [distribuição](https://aka.ms/wslstore) de sua escolha.

## <a name="start-debugging-with-wsl-2"></a>Iniciar Depuração com WSL 2

1. Depois de instalar os componentes necessários, abra um aplicativo Web ASP.NET Core ou aplicativo de console do .NET Core no Visual Studio você verá um novo perfil de inicialização chamado WSL 2:

   ![Perfil de inicialização do WSL 2 na lista de perfis de inicialização](media/linux-wsl2-debugging-select-launch-profile.png)

1. Selecione este perfil para adicioná-lo ao seu *launchSettings.jsem*.

   Alguns dos principais atributos no arquivo são mostrados no exemplo a seguir.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Depois de selecionar o novo perfil, a extensão verifica se sua distribuição do WSL 2 está configurada para executar aplicativos .NET Core e ajuda a instalar quaisquer dependências ausentes. Depois de instalar essas dependências, você estará pronto para depurar no WSL 2.

1. Inicie a depuração como normal e seu aplicativo será executado na distribuição padrão do WSL 2.

   Uma maneira fácil de verificar se você está executando no Linux é verificar o valor de `Environment.OSVersion` .

>[!NOTE]
> Somente o Ubuntu e o Debian foram testados e têm suporte. Outras distribuições com suporte do .NET Core devem funcionar, mas precisam instalar manualmente o tempo de execução e a [rotação](https://curl.haxx.se/)do [.NET Core](https://aka.ms/wsldotnet) .

## <a name="choose-a-specific-distribution"></a>Escolher uma distribuição específica

Por padrão, o perfil de inicialização WSL 2 usa a distribuição padrão, conforme definido em *wsl.exe*. Se desejar que seu perfil de inicialização Direcione para uma distribuição específica, independentemente desse padrão, você poderá modificar seu perfil de inicialização. Por exemplo, se você estiver depurando um aplicativo Web e quiser testá-lo no Ubuntu 20, 4, seu perfil de inicialização teria a seguinte aparência:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Direcionar várias distribuições

Indo um pouco além, se você estiver trabalhando em um aplicativo que precisa ser executado em várias distribuições e desejar uma maneira rápida de testar cada um deles, você pode ter vários perfis de inicialização. Por exemplo, se você precisar testar seu aplicativo de console no Debian, Ubuntu 18, 4 e Ubuntu 20, 4, poderá usar os seguintes perfis de inicialização:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Com esses perfis de inicialização, você pode alternar facilmente entre suas distribuições de destino, tudo sem deixar o conforto do Visual Studio.

![Vários perfis de inicialização WSL 2 na lista de perfis de inicialização](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Configurações de WSL no perfil de inicialização

A tabela a seguir mostra as configurações com suporte no perfil de inicialização.

|Nome|Padrão|Finalidade|Dá suporte a tokens?|
|-|-|-|-|
|executablePath|dotnet|O executável a ser executado|Sim|
|commandLineArgs|O valor da propriedade TargetPath do MSBuild mapeada para o ambiente WSL|Argumentos de linha de comando passados para executablePath|Sim|
|workingDirectory|Para aplicativos de console: {*OutDir*}</br>Para aplicativos Web: {*ProjectDir*}|O diretório de trabalho no qual iniciar a depuração|Sim|
|environmentVariables||Pares chave-valor das variáveis de ambiente a serem definidas para o processo depurado.|Sim|
|setupScriptPath||Script a ser executado antes da depuração. Útil para executar scripts como ~/.bash_profile.|Sim|
|distributionname||Nome da distribuição de WSL a ser usada.|Não|
|launchBrowser|false|Se deseja ou não iniciar um navegador|Não|
|launchUrl||URL a ser iniciada se launchBrowser for true|Não|

Tokens com suporte:

{*ProjectDir*}-o caminho para o diretório do projeto

{*OutDir*}-o valor da Propriedade MSBuild `OutDir`

>[!NOTE]
> Todos os caminhos são para WSL não Windows.
