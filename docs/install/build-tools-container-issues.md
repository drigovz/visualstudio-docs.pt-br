---
title: Problemas conhecidos de contêineres
description: Saiba mais sobre os problemas conhecidos que podem ocorrer quando as Ferramentas de Build do Visual Studio são instaladas em um contêiner do Windows.
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52e3ab107aac36f50307db910c71e03b5a8b439b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983696"
---
# <a name="known-issues-for-containers"></a>Problemas conhecidos de contêineres

Há alguns problemas ao instalar o Visual Studio em um contêiner do Docker.

::: moniker range="vs-2017"

## <a name="windows-container"></a>Contêiner do Windows

Estes problemas conhecidos ocorrem quando as Ferramentas de Build do Visual Studio 2017 são instaladas em um contêiner do Windows.

* Não é possível instalar o Visual Studio em um contêiner com base na imagem microsoft/windowsservercore:10.0.14393.1593. As imagens marcadas com versões do Windows anteriores ou posteriores à versão 10.0.14393 deverão funcionar.
* Não é possível instalar o SDK do Windows versão 10.0.14393 ou anterior. A instalação de certos pacotes falha e as cargas de trabalho que dependem desses pacotes não funcionarão.
* Passe `-m 2GB` (ou mais) ao compilar a imagem. Algumas cargas de trabalho exigem mais memória que o padrão de 1 GB quando instaladas.
* Configure o Docker para usar discos maiores que o padrão de 20 GB.
* Passe `--norestart` na linha de comando. A partir dessa gravação, tentar reiniciar um contêiner do Windows dentro do contêiner retorna `ERROR_TOO_MANY_OPEN_FILES` para o host.
* Se você basear sua imagem diretamente no microsoft/windowsservercore, o .NET Framework poderá não ser instalado corretamente e nenhum erro de instalação será indicado. Código gerenciado não poderá ser executado depois que a instalação for concluída. Em vez disso, baseie a imagem no [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) ou posterior. Por exemplo, você poderá ver um erro ao compilar com o MSBuild, como:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): erro MSB6003: Não foi possível executar o executável da tarefa especificada "csc.exe". Não foi possível carregar o arquivo ou assembly “System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" ou uma de suas dependências. O sistema não pode encontrar o arquivo especificado.

* Não é possível instalar o Visual Studio 2017 versão 15.8 ou anterior (qualquer produto) no mcr<span></span>.microsoft.com/windows/servercore:1809 ou posterior. Consulte https://aka.ms/setup/containers/servercore1809 para obter mais informações.

::: moniker-end

## <a name="build-tools-container"></a>Contêiner das Ferramentas de Build

Os problemas conhecidos a seguir podem ocorrer ao usar o contêiner das Ferramentas de Build. Para ver se os problemas foram corrigidos ou se há outros problemas conhecidos, visite https://developercommunity.visualstudio.com.

* O IntelliTrace pode não funcionar em [alguns cenários](https://github.com/Microsoft/vstest/issues/940) dentro de um contêiner.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar ferramentas de build em um contêiner](build-tools-container.md)
* [Exemplo avançado para contêineres](advanced-build-tools-container.md)
* [IDs de carga de trabalho e de componente das Ferramentas de Build do Visual Studio](workload-component-id-vs-build-tools.md)
