---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
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
ms.openlocfilehash: ed14c3ec0da75df37c5a006f4e25240ac6630d20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949648"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança, carregando apenas o ambiente e os serviços padrão.

## <a name="syntax"></a>Sintaxe

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Comentários
 Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é iniciado, garantindo assim uma execução estável.

## <a name="description"></a>Descrição
 O exemplo a seguir inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança.

## <a name="code"></a>Código

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)