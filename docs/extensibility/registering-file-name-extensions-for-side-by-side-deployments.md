---
title: Registrando extensões de nome de arquivo para implantações lado a lado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701551"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registre extensões de nome de arquivo para implantações lado a lado
Para VSPackages implantados em um ambiente lado a lado, você deve registrar extensões [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de nome de arquivo para associar os arquivos à versão correta de . A menos que você use uma extensão de nome de arquivo específica da versão, o registro permite que os usuários abram seus arquivos de itens de projeto e projeto na versão apropriada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Nesta seção
- [Sobre extensões de nome de arquivo](../extensibility/about-file-name-extensions.md) Discute como as extensões de nome do arquivo são registradas.

- [Especificar manipuladores de arquivos para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Fornece informações sobre como registrar os aplicativos que podem abrir, editar e assim por diante, uma extensão específica do nome do arquivo.

- [Registre verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md) Discute como registrar verbos.

- [Gerenciar associações de arquivos lado a lado](../extensibility/managing-side-by-side-file-associations.md) Discute como lidar com instalações lado a lado nas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quais uma determinada versão deve ser invocada para abrir um arquivo.

## <a name="related-sections"></a>Seções relacionadas
- [Suporte a várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Descreve problemas relacionados a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] várias versões e ao seu VSPackage durante o desenvolvimento e implantação para usuários finais.
