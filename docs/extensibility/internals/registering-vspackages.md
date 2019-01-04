---
title: Registrar VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4b5bedbfdeaab6fa3d7d8efe4479a8b7f3e4de4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842600"
---
# <a name="registering-vspackages"></a>Registrando VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se baseia em arquivos. pkgdef para descrever e localizar um VSPackage. Um arquivo. pkgdef contém todas as informações de registro caso contrário, seriam adicionadas ao registro do sistema. VSPackages gerenciados são registrados, adicionando atributos no código-fonte e, em seguida, executando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) no assembly resultante para gerar um arquivo. pkgdef.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Especificar o local do arquivo VSPackage ao Shell do VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descreve o caminho de carregamento de VSPackages.  
  
 [Registrar e cancelar o registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica como registrar um VSPackage.  
