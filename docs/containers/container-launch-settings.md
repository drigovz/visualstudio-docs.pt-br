---
title: Configurações de lançamento do Visual Studio Container Tools
author: ghogen
description: Visão geral do processo de compilação de ferramentas de contêiner
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 63cf881fdedf9608d5cb773bbcb6b969a0f51624
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472650"
---
# <a name="container-tools-launch-settings"></a>Configurações de lançamento do Container Tools

Na pasta *Propriedades* em um projeto ASP.NET Core, você pode encontrar o arquivo launchSettings.json, que contém configurações que controlam como seu aplicativo web é iniciado em sua máquina de desenvolvimento. Para obter informações detalhadas sobre como este arquivo é usado no desenvolvimento ASP.NET, consulte [Use vários ambientes em ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). No *launchSettings.json*, as configurações na seção **Docker** estão relacionadas à forma como o Visual Studio lida com aplicativos contêiner.

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

A configuração commandName identifica que esta seção se aplica a Ferramentas de contêiner. A tabela a seguir mostra as propriedades que podem ser definidas nesta seção:

::: moniker range="vs-2017"

|Nome da configuração|Versão|Exemplo|Descrição|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": verdadeiro|Indica se deve iniciar o navegador depois de iniciar com sucesso o projeto.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Esta URL é usada ao iniciar o navegador.  Os tokens de substituição suportados para esta seqüência são:<br>   {Esquema} - Substituído por "http" ou "https" dependendo se o SSL é usado.<br>   {ServiceHost} - Geralmente substituído por "localhost". Ao direcionar os contêineres do Windows no Windows 10 RS3 ou mais antigos, porém, ele é substituído pelo IP do contêiner.<br>   {ServicePort} - Geralmente substituído por sslPort ou httpPort, dependendo se o SSL é usado.  Ao direcionar os contêineres do Windows no Windows 10 RS3 ou mais antigos, porém, ele é substituído por "443" ou "80", dependendo se o SSL é usado.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nome da configuração         | Exemplo                                               | Descrição                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Commandlineargs      | "commandLineArgs": "-mysetting myvalue"              | Esses argumentos de linha de comando para iniciar seu aplicativo são usados ao iniciar seu projeto no contêiner.                                     |
| Environmentvariables | "ambienteVariáveis": {                             | Esses valores de variável de ambiente são passados para o processo quando ele é lançado no recipiente.                       |
|                      | "ASPNETCORE_URLS":https://+:443" ; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Esta porta no host é mapeada para o porto do contêiner 80 ao lançar o contêiner.                                |
|                      |                                                       | Se não especificado, o valor é retirado do valor iisSettings.                                                          |
| launchBrowser        | "launchBrowser": verdadeiro                                 | Indica se deve iniciar o navegador depois de iniciar com sucesso o projeto.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Esta URL é usada ao iniciar o navegador. Os tokens de substituição suportados para esta seqüência são:                          |
|                      |                                                       | - {Esquema} - Substituído por "http" ou "https" dependendo se o SSL é usado.                                   |
|                      |                                                       | - {ServiceHost} - Geralmente substituído por "localhost".                                                                    |
|                      |                                                       | Ao direcionar os contêineres do Windows no Windows 10 RS3 ou mais antigos, porém, ele é substituído pelo IP do contêiner.           |
|                      |                                                       | - {ServicePort} - Geralmente substituído por sslPort ou httpPort, dependendo se o SSL é usado.                   |
|                      |                                                       | Ao direcionar contêineres windows no Windows 10 RS3 ou mais antigos, porém, ele é substituído por "443" ou "80",         |
|                      |                                                       | dependendo se o SSL é usado.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Esta porta no host é mapeada para o porto do contêiner 443 ao lançar o contêiner.                               |
|                      |                                                       | Se não especificado, o valor é retirado do valor iisSettings.                                                          |
| Usessl               | "useSSL": verdadeiro                                        | Indica se deve usar SSL ao iniciar o projeto. Se o useSSL não for especificado, o SSL será usado quando sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Próximas etapas

Configure seu projeto definindo as [propriedades de compilação de ferramentas de contêiner](container-msbuild-properties.md).

## <a name="see-also"></a>Confira também

[Docker Compor propriedades de construção](docker-compose-properties.md)
