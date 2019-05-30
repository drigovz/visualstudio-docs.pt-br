---
title: Registrar VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ac51f23132d855c3da921cc2743c3064a353524
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331312"
---
# <a name="registering-vspackages"></a>Registrando VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se baseia em arquivos. pkgdef para descrever e localizar um VSPackage. Um arquivo. pkgdef contém todas as informações de registro caso contrário, seriam adicionadas ao registro do sistema. VSPackages gerenciados são registrados, adicionando atributos no código-fonte e, em seguida, executando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) no assembly resultante para gerar um arquivo. pkgdef.

## <a name="in-this-section"></a>Nesta seção
- [Especificar o local do arquivo VSPackage ao Shell do VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Descreve o caminho de carregamento de VSPackages.

- [Registrar e cancelar o registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explica como registrar um VSPackage.
