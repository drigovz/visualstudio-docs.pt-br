---
title: Desabilitar ou mover o cache do pacote
description: Saiba como desabilitar, habilitar ou mover o cache do pacote para implantações do Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 276eff442891f70b9eea76e9167b07f798af2d6a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591457"
---
# <a name="disable-or-move-the-package-cache"></a>Desabilitar ou mover o cache do pacote

O cache do pacote fornece uma origem de pacotes instalados, caso você precise reparar o Visual Studio ou outros produtos relacionados, em casos em não há conexão com a Internet. Com algumas unidades ou configurações de sistema, no entanto, não convém manter todos os pacotes.
O instalador os baixará quando necessário. Portanto, se você deseja salvar ou recuperar espaço em disco, pode desabilitar ou mover o cache do pacote.

## <a name="disable-the-package-cache"></a>Desabilitar o cache do pacote

Antes de instalar, modificar ou reparar o Visual Studio ou outros produtos com o novo instalador, você pode iniciar o instalador com a opção `--nocache` para o instalador.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Qualquer operação que você fizer em qualquer produto removerá quaisquer pacotes existentes para o produto e evitará salvar pacotes após a instalação. Se você modificar ou reparar o Visual Studio e pacotes forem necessários, serão baixados automaticamente e removidos após a instalação.

Se você quiser reabilitar o cache, passe `--cache` em vez disso. Somente os pacotes que são necessários serão armazenados. Portanto, se você precisar restaurar todos os pacotes, deverá reparar o Visual Studio antes de se desconectar da rede.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Você também pode definir a [política de registro](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads` para desabilitar o cache antes de instalar, modificar ou reparar o Visual Studio.

## <a name="move-the-package-cache"></a>Mover o cache do pacote

Uma configuração comum do sistema é ter o Windows instalado em um SSD com um disco rígido maior (ou mais) para necessidades de desenvolvimento, como código-fonte, binários de programa e muito mais. Se quiser trabalhar offline em vez disso, você poderá mover o cache do pacote.

No momento, você pode fazer isso somente se definir a [política de registro](set-defaults-for-enterprise-deployments.md) de `CachePath` antes de instalar, modificar ou reparar o Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Veja também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Definir padrões para implantações corporativas](set-defaults-for-enterprise-deployments.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
