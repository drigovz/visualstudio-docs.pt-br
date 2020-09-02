---
title: Localizando o Visual Studio | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7187fbcc3e3aca990846176676a47f5d17aaf00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64878151"
---
# <a name="locate-visual-studio"></a>Localizar o Visual Studio

A partir do Visual Studio 2017, você pode instalar várias instâncias da mesma versão ou até mesmo edição. Isso é útil quando você deseja visualizar a nova funcionalidade em seu computador de desenvolvimento primário enquanto mantém a instalação anterior. Devido a essas alterações, não há nenhuma variável de ambiente ou valor de registro que você pode usar para localizar uma instância. Em vez disso, você pode usar uma [API de consulta com](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) para localizar instâncias com base em critérios relevantes para sua extensão.

Essa é uma API rápida e somente leitura com pacotes NuGet disponíveis para código nativo e gerenciado.

| Código | Pacote |
| ---- | --- |
| Nativo | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Gerenciado | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Você pode localizar uma única instância, dado um caminho ou o processo atual, ou enumerar todas as instâncias. Consulte [nossos exemplos](https://github.com/Microsoft/vs-setup-samples) para obter exemplos completos de como localizar o Visual Studio.

## <a name="tools"></a>Ferramentas

Para encontrar o Visual Studio e outras ferramentas em ambientes de compilação, scripts do PowerShell, instaladores e mais cenários, há várias ferramentas de software livre que você pode usar diretamente ou redistribuir junto com seus próprios scripts.

| Projeto | Descrição |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Executável nativo de arquivo único para localizar instâncias que atendem a critérios como lançamento ou pré-lançamento, qual produto está instalado e quais cargas de trabalho são instaladas. Também dá suporte à localização do Visual Studio 2010 e mais recente, embora menos informações sejam retornadas para o Visual Studio 2017 e mais recente. Consulte o [wiki](https://github.com/Microsoft/vswhere/wiki) para obter exemplos. |
| [Cmdlets do VSSetup](https://github.com/Microsoft/vssetup.powershell) | Os cmdlets do PowerShell com suporte 2,0 e mais recentes que retornam informações ricas como objetos que você pode usar para localizar instâncias com base nos mesmos critérios que _vswhere_ e descobrir ainda mais propriedades sobre instâncias. Consulte o [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) para obter exemplos. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Localiza automaticamente _VSIXInstaller_ e passa a linha de comando para a instalação de um arquivo **. vsix* . Esse recurso pode ser útil em instaladores que não têm suporte direto para as APIs de consulta. Consulte o [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) para obter exemplos. |

## <a name="see-also"></a>Confira também

* [Alterações na instalação do Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Iniciar o Visual Studio usando DTE](launch-visual-studio-dte.md)