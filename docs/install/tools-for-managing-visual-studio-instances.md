---
title: Ferramentas para detectar e gerenciar instâncias do Visual Studio
titleSuffix: ''
description: Saiba mais sobre as ferramentas que você pode usar para detectar e gerenciar instalações do Visual Studio em computadores cliente.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d6e46c95584cb3732d6339a02f6098976f2bab85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115040"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Ferramentas para detectar e gerenciar instâncias do Visual Studio

Há várias ferramentas que você pode usar para detectar instalações do Visual Studio em computadores cliente, bem como para gerenciar as instalações.

## <a name="detecting-existing-visual-studio-instances"></a>Detectando instâncias existentes do Visual Studio

Tornamos várias ferramentas disponíveis que ajudarão você a detectar e gerenciar instâncias do Visual Studio instaladas em computadores cliente:

* [vswhere](https://github.com/microsoft/vswhere): um executável incorporado ao Visual Studio ou disponível para distribuição separada que ajuda você a encontrar a localização de todas as instâncias do Visual Studio em uma determinada máquina.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts do PowerShell que usam a API de Configuração de Instalação para identificar instâncias instaladas do Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): amostras do C# e C++ que demonstram como usar a API de Configuração de Instalação para consultar uma instalação existente.

Além disso, a [API de Configuração de Instalação](<xref:Microsoft.VisualStudio.Setup.Configuration>) fornece interfaces para desenvolvedores que desejam criar seus próprios utilitários para interrogar instâncias do Visual Studio.

## <a name="using-vswhereexe"></a>Usar o vswhere.exe

`vswhere.exe`é automaticamente incluído no Visual Studio (começando com visual studio 2017 versão 15.2 e versões posteriores), ou você pode baixá-lo a partir da [página vswhere releases](https://github.com/Microsoft/vswhere/releases). Use o `vswhere -?` para obter informações de ajuda sobre a ferramenta. Como exemplo, este comando mostra todas as versões do Visual Studio, incluindo versões mais antigas do produto e pré-lançamentos e gera os resultados no formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Para obter mais informações sobre a instalação do Visual Studio 2017, confira [Arquivos de Instalação do Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>A edição do Registro para uma instância do Visual Studio

No Visual Studio, configurações do Registro são armazenadas em um local privado, o que permite várias instâncias lado a lado no mesmo computador com a mesma versão do Visual Studio.

Como essas entradas não são armazenadas no Registro global, há instruções especiais para usar o Editor do Registro para fazer alterações nas configurações do Registro:

1. Se você tiver uma instância do Visual Studio aberta, feche-a.

1. Inicie o `regedit.exe`.

1. Selecione o nó `HKEY_LOCAL_MACHINE`.

1. No menu principal do Regedit, selecione **File** > **Load Hive...** e selecione o arquivo de registro privado, que é armazenado na pasta **AppData\Local.** Por exemplo: 

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` corresponde à instância do Visual Studio que você deseja procurar.

Você precisará fornecer um nome de hive, que se tornará o nome do hive isolado. Depois de fazer isso, você poderá pesquisar o Registro no hive isolado que criou.

> [!IMPORTANT]
> Antes de iniciar o Visual Studio novamente, você deve descarregar a seção isolada que criou. Para fazer isso, selecione **File** > **Unload Hive** no menu principal do Regedit. (Se você não fizer isso, o arquivo permanecerá bloqueado e o Visual Studio não poderá ser iniciado.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Confira também

* [Guia de Administradores do Visual Studio](visual-studio-administrator-guide.md)
