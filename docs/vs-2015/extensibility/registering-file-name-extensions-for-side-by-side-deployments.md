---
title: Registrando extensões de nome de arquivo para implantações lado a lado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163695"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrando extensões de nome de arquivo para implantações lado a lado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para o VSPackages implantado em um ambiente lado a lado, você deve registrar extensões de nome de arquivo para associar os arquivos com a versão correta do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . A menos que você use uma extensão de nome de arquivo específica de versão, o registro permite que os usuários abram o projeto e os arquivos de item de projeto na versão apropriada do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sobre as extensões de nome de arquivo](../extensibility/about-file-name-extensions.md)  
 Discute como as extensões de nome de arquivo são registradas.  
  
 [Especificar identificadores de arquivo para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fornece informações sobre como registrar os aplicativos que podem abrir, editar e assim por diante, uma extensão de nome de arquivo específica.  
  
 [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Discute como registrar verbos.  
  
 [Gerenciando associações de arquivo lado a lado](../extensibility/managing-side-by-side-file-associations.md)  
 Discute como lidar com instalações lado a lado nas quais uma versão específica do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deve ser chamada para abrir um arquivo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Fornecer suporte à várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descreve problemas relacionados a várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e seu VSPackage durante o desenvolvimento e a implantação para os usuários finais.
