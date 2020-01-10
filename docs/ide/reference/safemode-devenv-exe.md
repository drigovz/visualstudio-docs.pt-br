---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593584"
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

## <a name="see-also"></a>Veja também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
