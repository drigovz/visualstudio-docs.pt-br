---
title: Sobre extensões de nome de arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148029"
---
# <a name="about-file-name-extensions"></a>Sobre as extensões de nome de arquivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao registrar uma extensão de arquivo de um VSPackage, você o associa a uma versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Isso é importante se mais de uma versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estiver instalada em um computador.  
  
 As extensões de arquivo para VSPackages são registradas em HKEY_CLASSES_ROOT chave com um valor padrão que aponta para o identificador de programação (ProgID) associado.  
  
 Veja a seguir um exemplo das informações de registro para a extensão de arquivo. vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Os arquivos associados a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] devem ter um ProgID com versão, como `VisualStudio.vcproj.8.0` , para permitir que instalações lado a lado do produto mantenham associações de extensão de arquivo entre as versões do produto. Um ProgID específico da versão também permite que você use verbos padrão, como abrir, editar e assim por diante, sem a preocupação de substituir ou ser substituído por outros aplicativos ou versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Em determinados casos, o ProgID associado a uma extensão de arquivo não deve ser alterado. Por exemplo, o ProgID para a extensão de arquivo. htm (ProgID = HTMLFILE) é codificado em vários locais no sistema operacional e é amplamente conhecido e usado em associação com arquivos. htm e. html.  
  
## <a name="see-also"></a>Consulte Também  
 [Registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Especificar identificadores de arquivo para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
