---
title: Registrar VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924402"
---
# <a name="registering-vspackages"></a>Registrando VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se baseia em arquivos. pkgdef para descrever e localizar um VSPackage. Um arquivo. pkgdef contém todas as informações de registro caso contrário, seriam adicionadas ao registro do sistema. VSPackages gerenciados são registrados, adicionando atributos no código-fonte e, em seguida, executando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) no assembly resultante para gerar um arquivo. pkgdef.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Especificar o local do arquivo VSPackage ao Shell do VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descreve o caminho de carregamento de VSPackages.  
  
 [Registrar e cancelar o registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica como registrar um VSPackage.  
  
 [Usando um atributo de registro personalizado para registrar uma extensão](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Descreve como criar um manifesto de registro que pode ser usado para implantar um VSPackage gerenciado.
