---
title: Sobre extensões de nome de arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740351"
---
# <a name="about-file-name-extensions"></a>Sobre extensões de nome de arquivo
Quando você registra uma extensão de arquivo de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage, você o associa a uma versão de . Isso é importante se mais [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de uma versão do for instalado em um computador.

 As extensões de arquivo para VSPackages são registradas em **HKEY_CLASSES_ROOT** chave com um valor padrão que aponta para o identificador programático associado (ProgID).

 O exemplo a seguir mostra informações de registro para a extensão de arquivo *.vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Os arquivos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associados devem ter um ProgID versionado, como `VisualStudio.vcproj.8.0`. Um ProgID versão permite instalações lado a lado do produto para manter associações de extensão de arquivo entre as versões do produto. Um ProgID específico da versão também permite que você use verbos padrão, como abrir, editar e assim por diante, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sem a preocupação de substituir ou ser substituído por outros aplicativos ou versões de .

 Em certos casos, o ProgID associado a uma extensão de arquivo não deve ser alterado. Por exemplo, o ProgID para a extensão de arquivo *.htm* (progid = htmlfile) é codificado em vários lugares do sistema operacional, e é amplamente conhecido e usado em associação com arquivos *.htm* e *.html.*

## <a name="see-also"></a>Confira também
- [Registre extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Especificar manipuladores de arquivos para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
