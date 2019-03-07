---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938677"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Inicia o Visual Studio no modo de segurança, carregando apenas o ambiente e os serviços padrão.

## <a name="syntax"></a>Sintaxe

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Comentários

Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o Visual Studio é iniciado, garantindo assim uma execução estável.

## <a name="example"></a>Exemplo

O exemplo a seguir inicia o Visual Studio no modo de segurança.

```shell
devenv /safemode
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)