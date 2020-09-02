---
title: Registrando VSPackages | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157386"
---
# <a name="registering-vspackages"></a>Registrando VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depende de arquivos. pkgdef para descrever e localizar um VSPackage. Um arquivo. pkgdef contém todas as informações de registro que, de outra forma, seriam adicionadas ao registro do sistema. Os VSPackages gerenciados são registrados pela adição de atributos ao código-fonte e, em seguida, pela execução do [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) no assembly resultante para gerar um arquivo. pkgdef.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Especificando o local do arquivo do VSPackage para o Shell do VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descreve o caminho de carregamento para VSPackages.  
  
 [Registrar e cancelar o registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica como registrar um VSPackage.  
  
 [Usando um atributo de registro personalizado para registrar uma extensão](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Descreve como criar um manifesto de registro que pode ser usado para implantar um VSPackage gerenciado.
