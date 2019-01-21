---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 092cc1fc3267113e862646b7572e9091b8f6ddef
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227194"
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