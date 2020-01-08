---
title: Aplicar automaticamente as chaves do produto (Product Keys)
description: Saiba como aplicar chaves de produto de forma programática quando você implanta o Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d269102b4ab3edcf62a2101802c4731667b76eb7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567197"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio

É possível aplicar a chave do produto (Product Key) de forma programática como parte de um script usado para automatizar a implantação do Visual Studio. Você pode definir a chave do produto (Product Key) em um dispositivo de forma programática durante a instalação do Visual Studio ou após a conclusão de uma instalação.

## <a name="apply-the-license-after-installation"></a>Aplicar a licença após a instalação

::: moniker range="vs-2017"

É possível ativar uma versão instalada do Visual Studio com uma chave do produto (Product Key) usando o utilitário `StorePID.exe` nos computadores de destino no modo sem confirmação. `StorePID.exe` é um utilitário instalado com o Visual Studio 2017 no seguinte local padrão: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

É possível ativar uma versão instalada do Visual Studio com uma chave do produto (Product Key) usando o utilitário `StorePID.exe` nos computadores de destino no modo sem confirmação. `StorePID.exe` é um utilitário instalado com o Visual Studio 2019 no seguinte local padrão: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Execute `StorePID.exe` com privilégios elevados, usando um agente do System Center ou em um prompt de comandos com privilégios elevados. Em seguida, informe a chave do produto (Product Key) e o MPC (código de produto da Microsoft).

>[!IMPORTANT]
> Verifique se você incluiu os traços na chave do produto (Product Key).

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

O exemplo a seguir mostra uma linha de comando para aplicar a licença ao Visual Studio 2017 Enterprise, que tem um MPC de 08860, uma chave do produto (Product Key) `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` e pressupõe um local padrão para a instalação:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

O exemplo a seguir mostra uma linha de comando para aplicar a licença ao Visual Studio 2019 Enterprise, que tem um MPC de 09260, uma chave do produto (Product Key) `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` e pressupõe um local padrão para a instalação:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 A seguinte tabela lista os códigos MPC para cada edição do Visual Studio:

| Edição do Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Edição do Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

Se `StorePID.exe` aplicar a chave do produto (Product Key) com êxito, ele retornará um `%ERRORLEVEL%` de 0. Se encontrar erros, ele retornará um dos códigos a seguir, dependendo da condição de erro:

| Erro do                     | Código |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Quando você executa uma instância virtual do Visual Studio, certifique-se de também virtualizar a pasta AppData local e o registro. Para solucionar problemas de instâncias virtuais, execute `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe`.  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Veja também

* [Instalar o Visual Studio](../install/install-visual-studio.md)
* [Criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
